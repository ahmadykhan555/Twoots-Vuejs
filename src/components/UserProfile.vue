<template>
  <div class="user-profile flex p-4 items-start">
    <div class="flex flex-col justify-start">
      <UserInfoComponent :user="user" class="mb-4" />
      <NewTweetForm @createNewTweet="handleNewTweet"></NewTweetForm>
    </div>
    <TweetsList :tweets="user.tweets" :drafts="user.drafts" />
  </div>
</template>

<script>
import TweetsList from "./TweetsList.vue";

import UserInfoComponent from "./UserInfo.vue";
import NewTweetForm from "./NewTweetForm.vue";
export default {
  components: {
    TweetsList,
    NewTweetForm,
    UserInfoComponent,
  },
  data() {
    return {
      followers: 0,
      isLoading: false,
      user: {
        id: 1,
        username: "_ayk",
        firstName: "Ahmad",
        lastName: "Yar Khan",
        email: "",
        isAdmin: true,
        tweets: [
          {
            id: 1,
            content: "this is a sample tweet!",
          },
          {
            id: 2,
            content: "this is a 2nd sample tweet!",
          },
          {
            id: 3,
            content: "this is a 3rd sample tweet!",
          },
          {
            id: 4,
            content: "this is a 4th sample tweet!",
          },
        ],
        drafts: [],
      },
    };
  },

  methods: {
    followUser() {
      this.followers++;
    },
    markFavorite(args) {
      console.log(`Favorited tweet: ${args.id}`);
    },
    selectedType(value) {
      console.log(`type selected: ${value}`);
    },
    handleNewTweet({ content, type }) {
      console.log({ type });
      type === "draft" ? this.saveAsDraft(content) : this.saveNewTweet(content);
    },
    saveNewTweet(content) {
      this.user.tweets.unshift({
        id: this.user.tweets.length + 1,
        content: content,
      });
    },
    saveAsDraft(content) {
      console.log("Add as draft: ", content);
      this.user.drafts.unshift({
        id: this.user.tweets.length + 1,
        content: content,
      });
    },
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
};
</script>

<style>
</style>