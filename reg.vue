<template>
  <form @submit.prevent="submitForm">
    <input type="text" v-model="name" placeholder="Name" />
    <input type="email" v-model="email" placeholder="Email" />
    <input type="text" v-model="loveLanguage" placeholder="Love Language" />
    <button type="submit">Submit</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      email: "",
      loveLanguage: "",
      friends: [],
    };
  },
  methods: {
    submitForm() {
      const newFriend = {
        id: this.friends.length + 1,
        name: this.name,
        email: this.email,
        loveLanguage: this.loveLanguage,
      };

      // Convert the newFriend object to a JSON string
      const newFriendJSON = JSON.stringify(newFriend);

      this.$emit("newFriendAdded", newFriendJSON);
      // ... optional

      this.friends.push(newFriend);
      this.name = "";
      this.email = "";
      this.loveLanguage = "";
    },
  },
  provide() {
    return {
      friends: this.friends,
    };
  },
};
</script>
