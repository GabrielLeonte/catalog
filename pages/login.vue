<template>
  <div class="container">
    <div class="input-area">
      <div>
        <h1 class="title">Logheaza-te</h1>
        <input v-model="user" class="input" type="text" placeholder="Nume" />
        <input
          v-model="password"
          class="input"
          style="margin-top: 10px;"
          type="password"
          placeholder="Parola"
        />
        <button class="button" style="margin-top: 10px;" @click="login">
          <div v-if="user">Logheaza-te ca {{ user }}</div>
          <div v-else>Logheaza-te</div>
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped>
* {
  user-select: none;
  outline: none;
}
.input-area {
  margin: 0 auto;
  height: 100vh;
  padding: 0;
  display: flex;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: center;
}
img {
  margin-left: auto;
  margin-right: auto;
  display: block;
}

span {
  font-size: 40px;
  margin-left: auto;
  margin-right: auto;
  display: block;
}
button {
  display: block;
  position: fixed;
}
</style>

<script>
export default {
  layout: "basic",
  data() {
    return {
      user: "",
      password: ""
    };
  },
  methods: {
    login() {
      if (this.user === "") {
        alert("Te rog introdu un nume!");
      } else if (this.password === "") {
        alert("Te rog introdu o parola!");
      } else {
        if (this.user === "elev" && this.password === "copacelul") {
          this.$store.state.user = "elev";
          this.$router.push("/");
        } else if (this.user === "profesor" && this.password === "micutzu") {
          this.$store.state.user = "profesor";
          this.$router.push("/");
        } else {
          alert("Numele utilizatorului sau parola acestuia nu sunt corecte!");
        }
      }
    }
  }
};
</script>
