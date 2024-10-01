<template>
  <li v-for="(friend, index) in friends" :key="friend.id">
    <button @click="toggleFavorite(friend)">
      {{ friend.isFavorite ? "★" : "☆" }}
    </button>
    <button @click="toggleDetails(friend)">
      {{ friend.showDetails ? "Hide Details" : "Show Details" }}
    </button>
    <div v-if="friend.showDetails">
      {{ friend.name }} - {{ friend.email }}
      <ul>
        <li v-for="language in friend.loveLanguage" :key="language">
          {{ language }}
        </li>
      </ul>
    </div>
  </li>
</template>

<script>
export default {
  inject: ["friends"],
  data() {
    return {
      friends: [],
      isFavorite: false,
      showDetails: false,
    };
  },
  methods: {
    toggleFavorite(friend) {
      friend.isFavorite = !friend.isFavorite;
    },
    toggleDetails(friend) {
      friend.showDetails = !friend.showDetails;
    },
    deleteFriend(index) {
      this.friends.splice(index, 1);
    },
  },
  computed: {
    currentFriend() {
      return this.friends[this.friends.length - 1];
    },
  },
};
</script>
