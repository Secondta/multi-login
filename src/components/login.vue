<template>
<div>
  <div class="container d-flex justify-content-center">
    <div class="row">
      <div class="col">
          <center>
        <h1>Silahkan Login</h1></center><br><br>
        <center>
        <input v-model="username" style="border-radius: 20px; width: 8cm;" type="text" placeholder="Username"><br><br>
        <input v-model="password" style="border-radius: 20px; width: 8cm;" type="password" placeholder="Password"><br><br>
        <input style="border-radius: 20px; width: 8cm; background-color: white;" type="submit" value="Login" @click="login"><br>
        <a class="text-center" href="/register">Silahkan Registrasi</a>
        </center>
      </div>
    </div>
  </div>
</div>
</template>
    
<script>
import axios from "axios";  
export default {  
  name: "login",  
  data() {  
    return {  
      username: "",  
      password: "",  
      useres: [],  
    };  
  },  
  methods: {  
    async getUsers() {  
      const user = await axios.get("http://localhost:3000/users");  
      this.useres = user.data;  
    },  
    login() {  
      const login = this.useres.find(  
        (data) =>  
          data.username === this.username && data.password === this.password  
      );  
      if (login === undefined) {  
        alert("Username Or Password not found");  
      } else {  
        var convertToString = JSON.stringify(login); 
        sessionStorage.setItem("USER_DATA", convertToString); 
        this.$router.push("/");  
        window.location.reload();  
      }  
    },  
  },  
  mounted() {  
    this.getUsers();  
  },  
};  
</script>