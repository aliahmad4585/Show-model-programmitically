<template>
  <div id="app">
    <b-card title="Card Title" no-body>
      <b-card-header header-tag="nav">
        <b-nav id="h">
          <b-nav-item active @click="modalShow = !modalShow">Login</b-nav-item>
        </b-nav>
      </b-card-header>

      <b-card-body class="text-center">
        <b-card-text>
          private button can only access when login
        </b-card-text>

        <b-button variant="primary" @click="privateModel()">Private Button</b-button>
        <b-button variant="primary" @click="publiModel()">Public Button</b-button>
      </b-card-body>
    </b-card>
    <b-modal v-model="modalShow"
      ><b-container fluid>
        <b-row class="my-1">
          <b-col sm="2">
            <label for="input-default">Email:</label>
          </b-col>
          <b-col sm="10">
            <b-form-input
              id="input-default"
              placeholder="Enter your email"
              v-model="email"
            ></b-form-input>
            <br />
          </b-col>
          <b-col sm="2">
            <label for="input-default">Password:</label>
          </b-col>
          <b-col sm="10">
            <b-form-input
              id="input-default"
              placeholder="Enter your Password"
              v-model="password"
            ></b-form-input>
          </b-col>
        </b-row>
        <b-button variant="primary" @click="Login">Login</b-button>
      </b-container></b-modal>

       <b-modal v-model="pModelShow"> you are login in right now</b-modal>
         <b-modal v-model="ppModelShow"> You are access without login</b-modal>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      modalShow: false,
      pModelShow:false,
      ppModelShow:false,
      isLogged:false,
      email: "",
      password: ""
    };
  },
  methods: {
    Login() {
     this.isLogged=true;

    },
    publiModel(){
        this.ppModelShow = true;
    },
    privateModel(){
      if(this.isLogged){
        this.pModelShow=true;
      }
    }
  }
};
</script>
<style>
#h {
  float: right;
}
</style>
