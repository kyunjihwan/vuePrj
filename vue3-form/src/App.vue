<template>
  <form action="" @submit.prevent="submitForm">
    <div>
      <label for="userId">ID:</label>
      <input id="userId" type="text" v-model="userName" />
    </div>
    <div>
      <label for="password">PW:</label>
      <input id="password" type="text" v-model="password" />
    </div>
    <button type="submit">로그인</button>
  </form>
</template>

<script>
import axios from "axios";
import { ref } from "vue";

export default {
  setup() {
    // data
    var userName = ref("");
    var password = ref("");

    // methods
    var submitForm = () => {
      const data = { userName: userName.value, password: password.value };
      axios
        .post("https://jsonplaceholder.typicode.com/users/", data)
        .then((resp) => {
          console.log(resp);
        })
        .catch((err) => {
          console.log(err);
        });
      console.log("제출됨");
    };

    return { userName, password, submitForm };
  },
  // methods: {
  //   logText() {
  //     this.password
  //   }
  // }
  // data() {
  //   return {
  //     userName: "",
  //     password: "",
  //   };
  // },
  // methods: {
  //   submitForm() {
  //     const data = { userName: this.userName, password: this.password };
  //     axios
  //       .post("https://jsonplaceholder.typicode.com/users/", data)
  //       .then((resp) => {
  //         console.log(resp);
  //       })
  //       .catch((err) => {
  //         console.log(err);
  //       });
  //     console.log("제출됨");
  //   },
  // },
};
</script>

<style scoped></style>
