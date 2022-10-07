<template>

  <login-template>

    <span slot="menuesquerdo">
     <img src="https://cakeerp.com/wp-content/uploads/2019/10/girls-with-smartphone-social-profile-messages_24877-53929.jpg" 
     class="responsive-img">

    </span>

    <span slot="principal">

      <span>
        <h2>Login</h2>

        <input type="email" placeholder="E-mail" v-model="email">
        <input type="password" placeholder="Senha" v-model="password">
        <button type="button" class="btn green" v-on:click="login">Entrar</button>
        <router-link type="button" class="btn purple" to="/cadastro">Cadastre-se</router-link>
 
      </span>
    
    </span>

  </login-template>

</template>

<script>
import LoginTemplate from '@/templates/LoginTemplate'
import axios from 'axios';

export default {
  name: 'Login',
  data () {
    return {
     email:'',
     password:''
    }
  },
  components:{
    LoginTemplate,
  },
  methods: {
    login() {
      axios.post('http://localhost:8000/api/login', {
        email: this.email,
        password: this.password
      })
      .then(response => {
         //console.log(response)
         if(response.data.token){
          //Login com sucesso
          console.log('Login com sucesso')
          sessionStorage.setItem('usuario',JSON.stringify(response.data));
         }
         else if(response.data.status == false){
          //Login não existe
          console.log('Login não existe')
          alert('Login Inváido')
         }
         else{
          //Erro de validacão
          console.log('Erro de validação')
          let erros = '';
          for(let erro of Object.values(response.data)){
            erros += erro + "";
          }
          alert(erros)
         }
      })
      .catch(e => {
        console.log(e)
        alert('Erro! Tente novamente mais tarde.')
      })
    }
    }
  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
