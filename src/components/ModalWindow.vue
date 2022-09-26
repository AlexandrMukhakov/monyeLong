<template>
    <div>
        <div class="modal">
            <div class="modal-dialog" ref="modal-dialog">
                <div class="modal-content">
                    <form @submit.prevent="onSubmit($event.target.value)" class="forma">
                        <div @click="closeModal" data-close class="modal__close">&times;</div>
                        <div class="backCall"><strong>Обратный звонок</strong></div>
                        <p class="messe">Отправте ваши данные, что бы мой секретарь мог с вами связаться, но это не точно</p>
                        <label><a>Ваше имя</a></label>
                        <input @input="name = $event.target.value" class="client-name" type="text" placeholder='Иван Иванов' name='name'/>
                        <slot></slot>
                        <label><a>Ваш телефон</a></label>
                        <input @input="tel = $event.target.value, wrong($event.target.value)" class="client-phone" type="tel" value="+7" required>
                        <span class="spanInput">{{place }}</span>
                        <div class="send">
                            <button @click="openFeed" disabled class="form-bottom" type="submit">отправить</button>
                            <div class="modal__title">Я обязательно свяжусь с тобой, как только захочу</div>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>
</template> 

<script>
export default {
    name: "Modal-window",
    props: [],
    data() {
        return {
            buttActive: false,
            place: " ",
            name: "",
            tel: "",
        };
    },
    methods: {
        openFeed() {
            this.$emit('openFeed')
        },
        closeModal() {
            this.$emit("closeModal");
        },
        onSubmit() {
            this.closeModal();
            console.log([this.name, this.tel]);
        },
        wrong(value) {
            let butt = document.querySelector(".form-bottom");
            if (value[0] != "+") {
                this.place = "Номер должен начинаться с +7";
            }
            else if (value.length > 12) {
                this.place = "Слишком много цифр";
            }
            else if (value.length < 12) {
                this.place = "Слишком мало цифр";
            }
            else if (value.length === 12 && value[0] === "+") {
                this.place = " ";
                butt.removeAttribute("disabled");
            }
        }
    },
    mounted() {
        let vm = this;
        document.addEventListener("click", function (item) {
            if (item.target === vm.$refs["modal-dialog"]) {
                vm.closeModal();
            }
        });
    },

}
</script>


<style>



.spanInput {
    color:darkorange
}

.modal {
    width: 100%;
    height: 100%;
    position: absolute;
    left: 0;
    top: 0;
    background-color: rgba(0, 0, 0, .8);
    z-index: 1000;
    flex-direction: column;
    justify-content: center;
}

.modal-dialog {
    position: relative;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    padding: 20px 50px 20px 20px;
    overflow: auto;
    border: 11px;

}

.client-name {
    width: 100%;
    border-style: none;
    height: 50px;
    margin-bottom: 28px;
    padding: 0 15px;
    border-radius: 15px;
}

.client-phone {
    width: 100%;
    height: 50px;
    border-style: none;
    padding: 0 15px;
    border-radius: 15px;
}


.label a:hover {
    color: black;
    border-bottom: solid black 1px;
}

.client-name:focus::-webkit-input-placeholder {
    color: transparent
}

.client-name:focus::-moz-placeholder {
    color: transparent
}

.client-name:focus:-moz-placeholder {
    color: transparent
}

.client-name:focus:-ms-input-placeholder {
    color: transparent
}

.forma {
    height: 50px;
    width: 300px;
    border-radius: 15px;
    border-style: none;
    font-weight: 500;
    color: rgb(245, 244, 244);
    cursor: pointer;
}

.form-bottom {
    margin-top: 38px;
    display: flex;
    flex-direction: row;
    align-items: center;
    -webkit-transition-duration: 0.4s; /* Safari */
    transition-duration: 0.4s;
    height: 50px;
    cursor: pointer;
    border-radius: 50px;
}

.modal__close {
    width: 30px;
    position: absolute;
    left: 1150px;
    color: #fff;
}

.modal-dialog {
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
}

.modal-dialog {
    padding: 0 40px;
    display: flex;
    flex-direction: column;
    min-height: 500px;
}

.modal-content {
    animation: dropdown .5s;
    width: 430px;
    height: 450px;
    margin: 0 auto;
    background: linear-gradient(94.67deg, black 15.88%, #aae6ec 121.21%);
    border-radius: 20px;
    display: flex;
    flex-direction: column;
    color: #fff;
    font-size: 20px;
    padding: 10px;
}

@keyframes dropdown {
    from {
        opacity: 0;
        transform: translateY(-3000px);
    }

    to {
        opacity: 1;
        transform: translateY(0px);
    }
}

.buttonOn:hover {
    background-color: #4CAF50; /* Green */
    color: white;
}

.send {
    position: absolute;
    bottom: 220px;
}


















@media screen and (max-width: 576px) {

.modal {
    position: absolute;
    width: 576px;
    height: 900px;
    overflow: hidden;

}

.forma{
    position: relative;
    bottom: 150px;
}

.modal-content {
    position: relative;
    right: 48px;
    width: 450px;
    height: 600px;
    display: flex;
    justify-content: center;
}


.modal-dialog {
    display: flex;
    justify-content: center;
    width: 100%;
    height: 100%;
}


.client-name {

    position: relative;
    bottom: 100px;
    margin-bottom: 50px;

}

.client-phone {
    display: flex;
    justify-content: center;
    margin-bottom: 50px;
    position: relative;
    bottom: 100px;
}

.form-bottom {
    display: flex;
    justify-content: center;
    width: 150px;
    margin-top: 50px;
}

.send {
    position: absolute;
    top: 300px;
}

.modal__close {
    width: 130px;
    position: relative;
    left: 430px;
    bottom: 150px;
    color: #fff;
  
}

.messe {
    display: flex;
    justify-content: center;
    position: relative;
    bottom: 100px;
    margin-bottom: 50px;
}

.backCall{
    position: relative;
    bottom: 100px;
}
.spanInput {
    position: relative;
    bottom: 150px;
}
a {
    position: relative;
    bottom: 100px;
}


}
</style>