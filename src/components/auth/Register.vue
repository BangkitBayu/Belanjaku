<template>
  <section id="form-container">
    <h1 class="title">Selamat Datang Pengguna Baru</h1>
    <form action="" autocomplete="off" @submit.prevent="onSubmit">
      <div class="form-group">
        <input
          type="email"
          id="email"
          placeholder="Email"
          required
          v-model="email"
        />
        <span id="errorInfo" v-if="emailError"> {{ emailError }}</span>
      </div>
      <div class="form-group">
        <input
          type="text"
          id="username"
          placeholder="Username"
          required
          v-model="username"
        />
        <span id="errorInfo" v-if="usernameError"> {{ usernameError }}</span>
      </div>
      <div class="form-group">
        <input
          :type="checked ? 'text' : 'password'"
          id="password"
          placeholder="Password"
          required
          v-model="password"
        />
        <span id="errorInfo" v-if="passwordError"> {{ passwordError }}</span>
        <div id="showPasswordContainer">
          <input type="checkbox" id="showPassword" v-model="checked" />
          <label for="showPassword">Show password</label>
        </div>
      </div>
      <div class="form-group">
        <button
          type="submit"
          :disabled="!isFormValid"
          :style="isFormValid ? 'background : red; color : white;' : ''"
          id="submitBtn"
          @click="saveUser()"
        >
          Submit
        </button>
      </div>
    </form>
    <p>Sudah Punya Akun? <a href="#">Masuk</a></p>
  </section>
</template>

<script>
export default {
  name: "RegisterForm",
  data() {
    return {
      users: [],
      checked: "",
      email: "",
      username: "",
      password: "",
    };
  },
  computed: {
    emailError() {
      if (this.email.length == 0) {
        return "Email tidak boleh kosong";
      }
      return "";
    },

    usernameError() {
      if (this.username.length == 0) {
        return "Username tidak boleh kosong";
      } else if (this.username.length < 3) {
        return "Panjang minimum username adalah 3 karakter ";
      }
      return "";
    },

    passwordError() {
      if (this.password.length == 0) {
        return "Password tidak boleh kosong";
      } else if (this.password.length < 6) {
        return "Panjang minimum password adalah 6 karakter";
      }
      return "";
    },

    //Untuk mengecek apakah ada error jika tidak ada lanjut
    isFormValid() {
      return (
        this.emailError == "" &&
        this.usernameError == "" &&
        this.passwordError == ""
      );
    },
  },

  methods: {
    onSubmit(e) {
      e.preventDefault();
    },

    saveUser() {
      let data = {
        id: "user-" + new Date().getTime(),
        email: this.email,
        username: this.username,
        password: this.password,
        date: new Date().toISOString(),
      };

      if (this.users.push(data)) {
        localStorage.setItem("users", JSON.stringify(this.users));
        alert("Pengguna Baru Berhasil Daftar");
      }
    },
  },

  mounted() {
    console.log("mounted");
  },

  watch: {},
};
</script>

<style scoped>
#form-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 1rem;
  height: 100vh;
}

form {
  display: grid;
  row-gap: 1rem;
}

input {
  padding: 0.5rem;
  padding-inline-end: 2rem;
  border-radius: 5px;
  border-color: rgba(94, 91, 91, 0.827);
  border-width: 2px;
}

#showPasswordContainer {
  margin-top: 0.8rem;
  display: flex;
  gap: 0.2rem;
}

#submitBtn {
  border: none;
  margin-top: 0.5rem;
  border-radius: 5px;
  padding-block: 0.5rem;
  padding-inline: 5rem;
  cursor: pointer;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
  text-align: start;
}

#errorInfo {
  color: red;
}
</style>
