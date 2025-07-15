<template>
  <section id="form-container">
    <h1 class="title">Selamat Datang Pengguna Baru</h1>
    <form action="" method="post">
      <div class="form-group">
        <input type="emal" id="email" placeholder="Email" required />
      </div>
      <div class="form-group">
        <input type="text" id="username" placeholder="Username" required />
      </div>
      <div class="form-group">
        <input type="password" id="password" placeholder="Password" required />
        <div id="showPasswordContainer">
          <input type="checkbox" name="showPassword" id="showPassword" />
          <label for="showPassword">Show password</label>
        </div>
      </div>
      <div class="form-group">
        <button disabled="disabled" id="submitBtn">Submit</button>
      </div>
    </form>
  </section>
</template>

<script>
export default {
  name: "RegisterForm",
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
  margin-top: 0.5rem;
  border-radius: 5px;
  padding-block: 0.5rem;
  padding-inline: 5rem;
}
</style>
