<template>
  <h3>@{{ user.username }} - {{ fullName }}</h3>
  <p>
    <strong>Followers: {{ followers }}</strong>
  </p>
  <button
    @click="followUser"
    class="border-2 border-gray-600 px-6 py-1 rounded-lg"
  >
    Follow
  </button>
</template>

<script>
export default {
  data() {
    return {
      followers: 0,
      isLoading: false,
      user: {
        id: 1,
        username: "_ayk",
        firstname: "Ahmad",
        lastName: "Yar Khan",
        email: "",
        isAdmin: true,
      },
    };
  },
  // computed Properties
  // used for derived properties, also as usual memoized getters
  computed: {
    fullName() {
      return `${this.user.firstname} ${this.user.lastName}`;
    },
  },

  // watch: watches a data point and runs when the data changes => similar to useEffect from react
  watch: {
    followers(newCount, oldCount) {
      if (oldCount < newCount)
        console.log(
          `@${this.user.username} Gained a follower, from ${oldCount} to ${newCount}`
        );
    },
  },

  // methods: take in an object
  methods: {
    followUser() {
      this.followers++;
    },
  },

  // lifecycle hooks: created, mounted, destroyed etc
  beforeCreate() {
    console.log("beforeCreate");
  },

  created() {
    console.log("created");
  },

  beforeMount() {
    console.log("beforeMount");
  },

  mounted() {
    console.log("mounted");
    this.followUser();
  },

  beforeUpdate() {
    console.log("beforeUpdate");
  },

  updated() {
    console.log("updated");
  },

  activated() {
    console.log("activated");
  },

  deactivated() {
    console.log("deactivated");
  },

  beforeUnmount() {
    console.log("beforeUnmount");
  },

  unmounted() {
    console.log("unmounted");
  },
};
</script>

<style>
</style>