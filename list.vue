<template>
  <ul>
    <registration-form @submit="addFriend" />
    <frienddetails :friends="friends" />
  </ul>
</template>

<script>
import registrationForm from "./registrationForm.vue";
import frienddetails from "./frienddetails.vue";

export default {
  components: {
    registrationForm,
    frienddetails,
  },
  data() {
    return {
      friends: [],
    };
  },
  methods: {
    /**optional */
    addFriend(newFriend) {
      this.friends.push(newFriend);
    },
  },
};
</script>
