<template>
  <div class="container">
    <div class="header">
      <div class="nameCoach">
        {{q()}}
        <h1>Бизнес коуч</h1>
        <h2>Богатов Борис Бритва</h2>
        <h2>Научу гребсти бабло лопатой</h2>
      </div>
      <div class="butt">
        <span>Заказать обратный звонок</span>
        <button class="buttonOn" @click="modalShow">связаться</button>
      </div>

    </div>

    <ModalWindow v-if="visibModal" @closeModal="CloseModal" @openFeed='openFeed'>
    </ModalWindow>

    <FeedBack v-if="feed" />

    <div class="imgCoach">
      <img src="../assets/foto.jpg" />
    </div>
    <div>
      <strong class="moneyLong">Со мной вы будете</strong>
      <div class="coachingMoney">
        <div class="money">
        <p>Гребсти Бабло</p>
        <p>Рубить капусту</p>
        <p>Мутить Кэш</p>
      </div>
      </div>
    </div>
  </div>
</template>

<script>
import ModalWindow from "./ModalWindow.vue";
import FeedBack from "./FeedBack.vue";
export default {
  data() {
    return {
      visibModal: false,
      feed: false
    };
  },
  components: { ModalWindow, FeedBack },
  methods: {
    modalShow() {
      this.visibModal = true
    },
    CloseModal() {
      this.visibModal = false
    },
    openFeed() {
      this.feed = true
    },
    closeFeed() {
      this.feed = false
    },
    q() {
      if (this.feed) {
        setTimeout(() => {
          this.feed = false
        }, 3000)
      }
    }
  },

}
</script>

<style>
.header {
  grid-area: header;
  display: flex;
  justify-content: space-between;
  z-index: 1;
}

.nameCoach {
  grid-area: nameCoach;
  
}

.butt {
  grid-area: butt;
  cursor: pointer;
  position: absolute;
  top: 5px;
  right: 5px;
  display: flex;
  flex-direction: column;
  
}

.butt span {
  font-size: 20px;
  font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif
}

.buttonOn {
  -webkit-transition-duration: 0.4s;
  /* Safari */
  transition-duration: 0.4s;
  height: 50px;
  cursor: pointer;
  border-radius: 50px;

}

.buttonOn:hover {
  background-color: #4CAF50;
  /* Green */
  color: white;
}

.imgCoach {
  grid-area: imgCoach;
  display: flex;
  justify-content: center;
  position: relative;
  bottom: 160px;
}


img {
  width: 450px;
  height: 450px;
  border-radius: 200px;
}

.moneyLong {
  width: 500px;
  grid-area: moneyLong;
  display: flex;
  justify-content: center;
   position: relative;
  bottom: 145px;
  margin: auto;
  font-size: 50px;
  font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
  border: 1px solid black;
  border-radius: 200px;
  padding: 5px;
}

.coachingMoney{
  display: flex;
  justify-content: center;
  position: relative;
  top: -120px;
}

.money {
  grid-area: money;
  display: flex;
  justify-content: space-evenly;
  border: 1px solid black;
  padding: 5px;
  border-radius: 400px;
  margin-bottom: auto;
  font-size: 20px;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  width: 80%;
}


.container {
  display: grid;
  grid-template-areas: "header"
    'imgCoach'
    'moneyLong'
    'money';
}

@media screen and (max-width: 576px) {
  .header{
    display: flex;
    justify-content: center;
  }
  .imgCoach{
    display: flex;
    justify-content: center;
    margin-top: 150px;
  }
  .butt {
    display: flex;
    position: relative;
  }

  p {
    font-weight: bold;
  }
  .money{
    color:aliceblue;
  }

  }

</style>
