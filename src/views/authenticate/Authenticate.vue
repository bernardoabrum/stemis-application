<template>
  <div>
    <div class="authenticate-page">
      <Login />
      <Register />
      <div class="info">
        <p>
          Certifique-se de que o json-server esteja observando o arquivo db.json
          na porta 3000
        </p>
        <p>Primeiro crie uma ou mais contas e faça alguns agendamentos</p>
        <p>
          Depois, faça login usando email: "admin" e senha: "admin" para ter
          acesso a visão do barbeiro
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import "./Authenticate.scss";
import Register from "@/components/register/Register.vue";
import Login from "@/components/login/Login.vue";

export default {
  components: {
    Register,
    Login,
  },
};
</script>
