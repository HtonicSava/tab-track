<template>
  <div class="Register">
      <div class="Register__content">
        <div class="Register__windowWrapper">
            <div class="Register__window">
                <div class="Register__title">
                    <h1>Регистрация</h1>
                </div>
                <div class="Register__subtitle">
                    <h1>Введите свои данные:</h1>
                </div>
                <div class="Register__body">
                    <div class="Register__input">
                        <input 
                        v-model="email"
                        placeholder="e-mail" 
                        type="email">
                    </div>
                    <div class="Register__input">
                        <input 
                        v-model="password"
                        placeholder="пароль" 
                        type="password">
                    </div>
                    <div class="Register__input">
                        <input
                        v-model="repeatPassword" 
                        placeholder="повторите пароль" 
                        type="password">
                    </div>
                </div>
                <div class="Register__buttonsBody">
                    <button 
                    class="Register__button"
                    @click="registration"
                    :disabled='password.length < 6 || password != repeatPassword'
                    >
                        Зарегистрироваться
                    </button>
                </div>
                <div class="Register__footer">
                    <p>Уже есть аккаунт? </p> 
                    <a href="">Войти</a>
                </div>
            </div>
            <div v-if="password.length < 6 && showHintPasswordLength" class="Register__hint">
                <Hint @closeHint = "closeHintPasswordLength" v-bind:text="hintPasswordLength"/>
            </div>
            <div v-if="password != repeatPassword && showHintPassworEqual" class="Register__hint">
                <Hint @closeHint = "closeHintPasswordEqual" v-bind:text="hintPassworEqual"/>
            </div>
        </div>
      </div>
  </div>
</template>

<script>
import Hint from '@/components/hint'
import AuthenticationService from '@/services/AuthenticationService'

export default {
  name: 'Register',
  components: {
      Hint
  },
  props: {
  },
  data () {
      return {
          email:'',
          password:'',
          repeatPassword:'',
          hintPasswordLength: 'пароль должен быть не менее 6 символов',
          hintPassworEqual: 'пароли должны совпадать ',
          showHintPasswordLength: true,
          showHintPassworEqual: true
      }
  },
  methods: {
      async registration(){
         const response = await AuthenticationService.register({
              email: this.email,
              password: this.password
          })
          console.log(response.data)
      },
      closeHintPasswordLength(){
          this.showHintPasswordLength = false
      },
      closeHintPasswordEqual(){
          this.showHintPassworEqual = false
      }
  }
}
</script>

<style scoped>

.Register {
    height: 100vh;
    background: linear-gradient(209deg, rgba(34, 192, 195, 0.712) 0%, rgba(117, 145, 191, 0.466) 38%, rgba(253, 187, 45, 0.712) 100%);
    font-family: Arial, Helvetica, sans-serif;
}
.Register__content {
    height: 100%;
    max-width: 1220px;
    padding: 0px 10px;
    margin: auto;
    display: flex;
    /* align-items: center; */
    justify-content: center;

}
.Register__window {
    margin-top: 50px;
    background-color: rgba(255, 255, 255, 0.575);
    /* padding: 0px 15px; */
    border-radius: 5px;
    -webkit-box-shadow: 7px -7px 15px 1px rgba(34, 60, 80, 0.35);
    -moz-box-shadow: 7px -7px 15px 1px rgba(34, 60, 80, 0.35);
    box-shadow: 7px -7px 15px 1px rgba(34, 60, 80, 0.35);
}
.Register__title {

    display: flex;
    align-items: center;
    justify-content: center;
    border-top-left-radius: 5px;
    border-top-right-radius: 5px;
    background-color: rgb(255, 255, 255);
    padding: 5px 15px 0px 15px;
    color: rgb(18, 33, 128);
    font-weight: 600;
    font-size: 24px;
    font-family: Arial, Helvetica, sans-serif

}

.Register__subtitle {

    display: flex;
    align-items: center;
    justify-content: center;
    background-color: rgb(255, 255, 255);
    padding: 5px 15px;
    color: rgb(18, 33, 128);
    font-weight: 600;
    font-size: 16px;
    

}
.Register__body {
    display: flex;
    align-items: center;
    flex-direction: column;
    padding: 30px 25px 20px 25px;
}
.Register__input input {
    background-color: rgb(255, 255, 255);
    padding: 5px;
    border-radius: 5px;
    color: black;
    border: 1px solid  rgb(255, 255, 255);
    margin-bottom: 16px;
}

.Register__input input:focus {
    background-color: rgba(91, 129, 172, 0.5);
    padding: 5px;
    border-radius: 5px;
    color: black;
    border: 1px solid #fff ;
    
}

.Register__input:first-child {
    margin-bottom: 0px;
}

.Register__buttonsBody{
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    padding-bottom: 16px;
}

.Register__button {
    padding: 10px;
    border-radius: 5px;
    color: #fff;
    background-color: rgba(0, 48, 102, 0.829);
    transition: 0.5s;
    font-weight: 700;
    font-size: 14px;
}

.Register__button:disabled{
    background-color: rgba(0, 48, 102, 0.246)
}

.Register__button:disabled:hover{
    background-color: rgba(0, 48, 102, 0.246);
    cursor: not-allowed;
}

.Register__button:hover {
    background-color: rgb(91, 129, 172);
}

.Register__footer{
  color: rgb(18, 33, 128);
  display: flex;
  align-items: center;
  flex-direction: column;
}

.Register__footer p{
    font-size: 14px;
    font-weight: 700;
    margin-bottom: 8px;

}

.Register__footer a{
    margin-bottom: 16px;
}

.Register__hint{
    max-width: 231px;
    width: 100%;
    /* position: absolute; */
}

</style>