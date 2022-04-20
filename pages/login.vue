<template>
  <section>
    <div class="login-container">
      <h1 class="title">{{ currentTitle }}</h1>
      <div class="loggedin">
        User Logged In:<strong> {{ isLoggedIn }} </strong>
      </div>
      <div class="formContainer" id="sawo-container" v-if="!isLoggedIn">
        <!-- The div in which sawo form is displayed -->
      </div>
      <div class="show-payload" v-if="isLoggedIn">
        <div class="show-payload-bg">
          <h3>User Successful Login</h3>
          <span>UserId: {{ userPayload.user_id }}</span>
          <br />
          <span>Verification Token: {{ userPayload.verification_token }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Sawo from "sawo";
export default {
  name: "Sawo",
  data: () => ({
    isLoggedIn: false,
    currentTitle: "SAWO NUXT Example App",
    userPayload: {},
    Sawo: null,
  }),
  mounted() {
    const config = {
      // should be same as the id of the container
      containerID: "sawo-container",
      // can be one of 'email' or 'phone_number_sms'
      identifierType: "email",
      // Add the API key
      apiKey: process.env.NUXT_ENV_SAWO_API_KEY,
      // Add a callback here to handle the payload sent by sdk
      onSuccess: (payload) => {
        this.userPayload = payload;
        this.isLoggedIn = true;
        this.currentTitle = "Dashboard";
      },
    };
    this.Sawo = new Sawo(config);
    this.Sawo.showForm();
  },
};
</script>

<style>
.login-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: #fff;
  height: 100vh;
}

.formContainer {
  padding: 1rem;
  height: 300px;
  width: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.show-payload-bg {
  color: #155724;
  background-color: #d4edda;
  border-color: #c3e6cb;
  padding: 10px;
  border-radius: 10px;
}

.loggedin{
  margin-bottom: 1rem;
}

@media (max-width: 400px) {
  #sawo-container {
    width: 100%;
  }
}
</style>
