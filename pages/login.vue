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
.container img {
  flex: 0.6;
  object-fit: contain;
}

.login-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f9f9f9;
}

.login-container h1 {
  font-weight: 500;
  font-size: 40px;
  color: #1f1e1e;
}

.login-container p {
  padding: 0 10px 0 10px;
  text-align: center;
}

.formContainer {
  padding: 1rem;
  background-color: #f3f3f3;
  border-radius: 10px;
  height: 300px;
  width: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.loggedin {
  margin-bottom: 10px;
}

.show-payload {
  padding: 1rem;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  height: 300px;
}

.show-payload-bg {
  color: #155724;
  background-color: #d4edda;
  border-color: #c3e6cb;
  padding: 10px;
  border-radius: 10px;
}

@media (max-width: 400px) {
  .container img {
    display: none;
  }

  .login-container {
    border: none;
    flex: 1;
  }

  #sawo-container {
    background-color: #bcedef;
    width: 100%;
  }
}
</style>
