<template>
<div>
  <div class="container d-flex justify-content-center">
    <div class="row">
      <div class="col">
          <center>
        <h1>Silahkan Registrasi</h1><br><br>
        <input v-model="username" style="border-radius: 20px; width: 8cm;" type="text" required placeholder="Username"><br><br>
        <input v-model="password" style="border-radius: 20px; width: 8cm;" type="password" required placeholder="Password"><br><br>
        <input style="border-radius: 20px; width: 8cm; background-color: white;" type="submit" value="Registrasi" @click="login">
        </center>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import axios from "axios"
export default {
    name: "register",
    data() {
        return {
            username: "",
            password: "",
            users: []
        }
    },
    methods: {
        async login() {
            const payload = {
                username: this.username,
                password: this.password,
                role: "siswa"
            };
            const register = await axios.post("http://localhost:3000/users", payload);
            var convertToString = JSON.stringify(register.data)
            sessionStorage.setItem("USER_DATA", convertToString);
            this.$router.push("/login");
        },
    },
};
</script>