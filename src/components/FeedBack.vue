<template>
    <div>
        <div class="feedBack">
            <div class="modal-dialogMess" ref="modal-dialogMess">
                <div class="modal-contentMess">
                    <strong class="mess">Спасибо! С первыми лучами солнца я с вами свяжусь</strong>
                </div>
            </div>
        </div>
    </div>
</template>



<script>
export default {
    data() {
        

    },
}
</script>


<style>
    .mess{
        font-size: 40px;
        display: flex;
        justify-content: center;
        align-items: center;
    }
.feedBack {
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

.modal-dialogMess {
    position: relative;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    padding: 20px 50px 20px 20px;
    overflow: auto;
    border: 11px;

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



.modal__close {
    width: 30px;
    position: absolute;
    right: 610px;
    color: #fff;
}

.modal-dialogMess {
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
}

.modal-dialogMess {
    padding: 0 40px;
    display: flex;
    flex-direction: column;
    min-height: 500px;
}

.modal-contentMess {
    animation: dropdown .5s;
    width: 540px;
    height: 120px;
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

</style>