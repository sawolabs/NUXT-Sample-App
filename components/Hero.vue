<template>
  <div>
    <div class="container">
      <nav
        class="navbar nav-m navbar-light primary-menu"
        style="background-color: #fff; justify-content: space-between"
      >
        <a class="navbar-brand" href="#"
          ><img class="navbar-logo" src="../assets/logo.jpg"
        /></a>
        <ul class="navbar-links">
          <li><a class="/" href="/">Home</a></li>
          <li><a href="/">Pricing</a></li>
          <li><a href="/">Docs</a></li>
          <li><a href="/">Resources</a></li>
          <li><a href="/">Contact Us</a></li>
          <li style="float: right">
            <Nuxt-link to="/login">
              <a class="btn1 btn-warning" type="button"> Login</a></Nuxt-link
            >
          </li>
        </ul>
        <div class="small-screen-navlink">
            <a class="btn1 btn-warning" type="button" href="/login"> Login</a>
        </div>
      </nav>
    </div>
    <main>
      <div class="heading">
        <h1>Product Headline</h1>
        <button class="btn btn-lg btn-warning mt-3 cta">
          <span>Call To Action</span>
        </button>
      </div>
      <div class="feature-cards row">
        <div class="">
          <div class="card">
            <div class="card-body">
              <h4 class="card-title">Feature One</h4>
              <p class="card-text">
                Some quick example text to build on the card title and make up
                the bulk of the card's content.
              </p>
              <a href="#" class="btn1 btn-warning">Go somewhere</a>
            </div>
          </div>
        </div>
        <div class="">
          <div class="card">
            <div class="card-body">
              <h4 class="card-title">Feature Two</h4>
              <p class="card-text">
                Some quick example text to build on the card title and make up
                the bulk of the card's content.
              </p>
              <a href="#" class="btn1 btn-warning">Go somewhere</a>
            </div>
          </div>
        </div>
        <div class="">
          <div class="card">
            <div class="card-body">
              <h4 class="card-title">Feature Three</h4>
              <p class="card-text">
                Some quick example text to build on the card title and make up
                the bulk of the card's content.
              </p>
              <a href="#" class="btn1 btn-warning">Go somewhere</a>
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: "Hero",
  methods: {
    home() {
      window.location.href = "/login";
    },
  },
};
</script>

<style>
.container {
  margin: 0;
  padding: 0;
  box-shadow: 0 8px 8px #888888;
}

.nav-m {
  background-color: #fff !important;
  display: flex;
  align-items: center;
}

.login {
  background-color: #ffa500;
  padding: 0.5rem;
}
.container {
  margin: 0;
  padding: 0;
  max-width: 100%;
  box-shadow: 0 8px 8px #888888;
}

body {
  background-image: url("../assets/bg.png");
  background-repeat: initial;
  background-size: cover;
  margin: 0;
  font-family: "Lato";
}

ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background-color: white;
}

.navbar-links {
  display: flex;
  align-items: center;
}

.small-screen-navlink {
  display: none;
}

li a {
  display: block;
  color: #888888;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

.active {
  color: #1a1a1a;
}

.btn {
  background-color: rgb(255, 222, 64);
  border: none;
  color: black;
  padding: 13px 30px;
  text-align: center;
  display: inline-block;
  font-size: 16px;
  margin: 1%;
  border-radius: 5px;
}

.btn1 {
  background-color: rgb(255, 222, 64);
  border: none;
  color: black;
  padding: 10px;
  text-align: center;
  display: inline-block;
  font-size: 16px;
  margin: 1%;
  text-decoration: none;
  border-radius: 5px;
}

.nav {
  padding-left: 2% !important;
  padding-right: 2% !important;
}

.navbar-brand {
  width: 100px;
  height: 80px;
}

.navbar-logo {
  margin: 8px;
  height: 4em;
  width: 4em;
  float: left;
}

main {
  height: 500px;
}

.heading {
  margin-top: 3rem;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.cta {
  transition: all 0.5s;
}

.cta span {
  cursor: pointer;
  display: inline-block;
  position: relative;
  transition: 0.5s;
}

.cta span:after {
  content: "\00bb";
  position: absolute;
  opacity: 0;
  top: 0;
  right: -20px;
  transition: 0.5s;
}

.cta:hover span {
  padding-right: 25px;
}

.cta:hover span:after {
  opacity: 1;
  right: 0;
}

.feature-cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-content: space-around;
  align-items: center;
  flex-direction: row;
}

.nav-link:active {
  color: #000000;
}

.card {
  border-radius: 10px;
  margin: 1rem;
  background-color: #ffffff;
  width: 20em;
  height: 200px;
  font-family: "Open Sans", sans-serif;
}
.card-body {
  padding: 3% 3%;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  height: 100%;
}

@media screen and (max-width: 720px) {
  .navbar-links {
    display: none;
  }
  .small-screen-navlink {
    display: flex;
    margin: 1rem;
  }
}
</style>
