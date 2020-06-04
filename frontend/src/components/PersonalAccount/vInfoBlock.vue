<template>
    <form class="info-block" @submit="submitFunc">
        <div class="info-block__section" v-for="input of formList" :key="input.id">
            <label :for="input.name" class="info-block__title">{{input.title}}</label>
            <input :type="input.type" :value="input.value" :id="input.name" :name="input.name" :class="['info-block__input',{activeInput: input.editInput} ]" :readonly="!input.editInput">
            <transition name="fade"> 
                <button class="info-block__edit" @click="editMode(input)"  v-show="!input.editInput">
                    <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path fill-rule="evenodd" clip-rule="evenodd" d="M20.71 4.04205C21.1 3.6521 21.1 3.02219 20.71 2.6322L18.37 0.29245C18.1832 0.105225 17.9295 0 17.665 0C17.4005 0 17.1469 0.105225 16.96 0.29245L15 2.25226L18.75 6.00186L20.71 4.04205ZM4 13.2511L14 3.25214L17.75 7.00174L7.75 17.0007H4V13.2511ZM6 15.0009H6.91998L14.92 7.00174L14 6.08185L6 14.081V15.0009ZM24 20.0004H0V24H24V20.0004Z"  fill-opacity="0.54"/>
                    </svg>
                </button>
            </transition>
            <transition name="fade">
                <div class="info-block__save-change" v-show="input.editInput">
                    <button class="btn" @click="input.editInput=!input.editInput">Сохранить</button>
                    <button class="btn-reverse" @click="input.editInput=!input.editInput">Отменить</button>
                </div>
            </transition>
        </div>
    </form>
</template>

<script>
export default {
    props:{
        info:{
            type: Object
        }
    },
    name: "tab-info-block",
    data(){
        return {
            formList:[
                 {
                    id: 1,
                    name: "surname",
                    title: "Фамилия",
                    type: "text",
                    editInput: false,
                    value: "Наумова",
                },
                {
                    id:2,
                    name: "name",
                    title: "Имя",
                    type: "text",
                    editInput: false,
                    value: "Валентина",
                },
                {
                    id:3,
                    name: "middleName",
                    title: "Отчество",
                    type: "text",
                    editInput: false,
                    value: "Дмитриевна",
                },
                {
                    id:4,
                    name: "password",
                    title: "Пароль",
                    type: "password",
                    editInput: false,
                    value: "12345",
                },
                {
                    id:5,
                    name: "email",
                    title: "E-mail",
                    type: "text",
                    editInput: false,
                    value: "veta92@gmail.com",
                },
                {
                    id:6,
                    name: "mobilePhone",
                    title: "Мобильный телефон",
                    type: "text",
                    editInput: false,
                    value: "+79190305456",
                },
               
            ],
        }
    },
    methods:{
        submitFunc(e){
          e.preventDefault();
        },
        editMode(input){
            input.editInput=!input.editInput
            this.formList.forEach(el=>el.id==input.id ? "" : el.editInput=false)
        }

    },
    
}
</script>

<style lang="scss">
    .info-block{
        padding-top: 30px;
        width: 100%;
        display: flex;
        flex-direction: column;
        &__section{
            max-width: 500px;
            width: 100%;
            display: flex;
            flex-wrap: wrap;
            //margin-bottom: 30px;
        }
        &__title{
            font-family: $font-arimo;
            font-size: 18px;
            width: 100%;
            margin-bottom: 14px;
            padding-left: 10px;
        }
        &__input{
            font-family: $font-arimo;
            width: 70%;
            font-size: 18px;
            border-color: transparent;
            color: lighten($color: $color-light-grey, $amount: 30%);
            font-weight: lighter;
            margin-bottom: 10px;
            &:focus{
                border-color: transparent;
            }
        }
        .activeInput{
            border-color: lighten($color: $color-light-grey, $amount: 30%);;
            &:focus{
                border-color:$color-cyan
            }
        }
        &__edit{
            width: 30%;
            padding: 0 20px;
            height: 30px;
            background: none;
            outline: none;
            border-bottom: 1px solid lighten($color: $color-light-grey, $amount: 30%);
            color: $color-cyan;
            border: none;
            svg{
                transition: fill .3s;
               fill: $color-light-grey;
               &:hover{
                fill: $color-cyan;
                }
            }
            
        }
        &__save-change{
            display: flex;
            justify-content: center;
            width: 70%;
            margin-bottom: 10px;
            button{
                margin: 0px 20px;
            }
            .btn,
            .btn-reverse{
                width: 130px;
                height: 35px;
                border-radius: 23px;
                font-size: 15px;
            }
        }
        &__data{
            display: flex;
            flex-direction: column;
            border-top: 1px solid lighten($color: $color-light-grey, $amount: 30%);
            background-color: $color-smoke;
            
            span{
                padding: 10px;
                font-size: $font-size;
                color: $color-medium-gray;
                font-family: $font-montserrat;
                
                border-bottom: 1px solid lighten($color: $color-light-grey, $amount: 30%) ;
            }
        }
        &__edit{
            button{
                padding: 9px 20px;
                border: none;
                background: none;
                outline: none;
                border-bottom: 1px solid lighten($color: $color-light-grey, $amount: 30%);
                color: $color-cyan;
            }
        }
        .fade-enter-active, .fade-leave-active {
            transition: opacity .3s;
        }
        .fade-enter, .fade-leave-to{
            opacity: 0;
        }
    }
    @media screen and (max-width: 650px){
        .info-block__save-change{
            .btn,
            .btn-reverse{
                font-size: 11px;
                height: 30px;
            }
        }
    }
</style>