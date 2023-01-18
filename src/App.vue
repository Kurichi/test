<script lang="ts">
export default {
  data() {
    return {
      title: "My New Vue Title",
      message: "Hello World",
      textStatus: {
        red: true,
      },
      input: {
        givenName: "",
        familyName: "",
        isMember: true,
      },
      users: [
        {
          givenName: "John",
          familyName: "Smith",
          isMember: true,
        },
        {
          givenName: "Taro",
          familyName: "Shinjuku",
          isMember: false,
        },
        {
          givenName: "Hanako",
          familyName: "Shibuya",
          isMember: true,
        },
      ],
    };
  },

  methods: {
    addUser() {
      this.users.push(this.input);
      this.input = {
        givenName: "",
        familyName: "",
        isMember: true,
      };
    },
  },
};
</script>

<template>
  <h1 :title="message" :class="textStatus">{{ title }}</h1>
  <input type="text" v-model="input.givenName" />
  <input type="text" v-model="input.familyName" />
  <input type="checkbox" v-model="input.isMember" />
  <button @click="addUser">ユーザの追加</button>

  <h2>ユーザのデータ</h2>
  <div v-for="user in users">
    <p>Name: {{ user.givenName + " " + user.familyName }}</p>
    <p v-if="user.isMember">メンバーです</p>
    <p v-else="user.isMember">メンバーではありません</p>
  </div>
</template>

<style>
.red {
  color: red;
}
</style>
