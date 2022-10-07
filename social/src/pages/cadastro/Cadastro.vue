<template>

  <login-template>

    <span slot="menuesquerdo">
     <img src="https://cakeerp.com/wp-content/uploads/2019/10/girls-with-smartphone-social-profile-messages_24877-53929.jpg" 
     class="responsive-img">

    </span>

    <span slot="principal">

      <span>
        <h2>Cadastro</h2>

        <input type="text" placeholder="Nome" value="">
        <input type="text" placeholder="E-mail" value="">
        <input type="text" placeholder="Senha" value="">
        <input type="text" placeholder="Repita a Senha" value="">
        <button type="button" class="btn green">Enviar</button>
        <router-link type="button" class="btn purple" to="/login" >Fazer Login</router-link>

      </span>
    
    </span>

  </login-template>

</template>

<script>
import LoginTemplate from '@/templates/LoginTemplate'

export default {
  name: 'Cadastro',
  data () {
    return {
      
    }
  },
  components:{
    LoginTemplate,
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
