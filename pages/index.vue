<template>
  <section>
    <div class="content">
      <img src="~/assets/images/backlog.events.png">
      <h1>Любим продуктовое комьюнити с 2019</h1>
      <h2>Следите за обновлениями — будет бомба 💣</h2>
      <form
        v-if="showForm"
        @submit.prevent="sendEmail">
        <input
          v-model="email"
          type="email"
          placeholder="Ваша электронная почта"
          required>
        <button
          type="submit">Заинтриговали</button>
      </form>
      <p
        v-if="success"
        class="success">Спасибо! Будем на связи ✌️🎉😘</p>
      <p
        v-if="error"
        class="error">О нет, что-то пошло не так! 😡</p>
    </div>
    <footer>
      <ul>
        <li class="facebook">
          <a href="https://www.facebook.com/backlog.events/">Facebook</a>
        </li>
        <li class="email">
          <a href="mailto:pv@backlog.events">Напишите нам</a>
        </li>
        <li class="copyright">
          © 2018 Backlog.Events
        </li>
      </ul>
    </footer>
  </section>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      showForm: true,
      email: '',
      error: false,
      success: false
    }
  },
  methods: {
    sendEmail: async function () {
      try {
        await axios.post('https://hooks.zapier.com/hooks/catch/4701579/nqmu53/', {
          email: this.email
        }, {
          headers: {
            'Content-Type': 'application/x-www-form-urlencoded'
          }
        });
        this.success = true
      } catch (e) {
        this.error = true
      }
      this.showForm = false
    }
  }
}
</script>

<style scoped>
* {
  font-family: Roboto;
}
html {
  height: 100%;
}
section {
  min-height: 100%;
  display: grid;
  grid-template-rows: 1fr auto;
}
footer {
  grid-row-start: 2;
  grid-row-end: 3;
  padding: 32px 0;
}
section {
  height: 100vh;
  /* width: 100%; */
  padding-left: 325px;
}
.content {
  padding-top: 140px;
}
h1 {
  margin-top: 1.2em;
  font-weight: 800;
  font-size: 72px;
  line-height: 72px;
  max-width: 800px;
  margin-bottom: 0;
}
h2 {
  margin-top: 1.5em;
  font-style: normal;
  font-weight: 500;
  font-size: 24px;
  line-height: 28px;
  margin-bottom: 0;
}
form {
  margin-top: 50px;
}
input[type=email] {
  width: 270px;
  height: 52px;
  padding-left: 16px;
  background: #FFFFFF;
  border: 1px solid rgba(0, 0, 0, 0.2);
  box-sizing: border-box;
  border-radius: 3px;
}
input::placeholder {
  position: relative;
  color: rgba(0, 0, 0, 0.36);
}
button {
  box-shadow: 0px 4px 8px rgba(104, 95, 240, 0.24), 0px 1px 1px rgba(104, 95, 240, 0.12);
  width: 160px;
  height: 52px;
  background: #685FF0;
  border: 1px solid #685FF0;
  box-sizing: border-box;
  border-radius: 3px;
  color: white;
  font-size: 15px;
  padding-top: 4px;
}
ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
ul > li {
  float: left;
  font-weight: 500;
  font-size: 15px;
  line-height: 20px;
  padding-right: 32px;
}
ul > li > a {
  text-decoration: none;
  color: #685FF0;
}
ul > li > a:hover {
  opacity: 0.8;
}
ul > li:last-child {
  float: right;
  margin-right: 500px;
}
.success, .error {
  font-style: normal;
  font-weight: 500;
  font-size: 24px;
  line-height: 24px;
  margin-top: 64px;
}
</style>
