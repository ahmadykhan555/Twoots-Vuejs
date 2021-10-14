<template>
  <div class="flex flex-col flex-1">
    <div class="flex-1 px-4 pb-4 ml-6 mb-4" v-if="tweets.length">
      <h3 class="font-bold text-left mb-2">Tweets</h3>
      <TweetItem v-for="tweet in tweets" :key="tweet.id" :tweet="tweet" />
    </div>
    <div class="flex-1 p-4 ml-6" v-if="drafts.length">
      <h3 class="font-bold text-left mb-2">Drafts</h3>
      <TweetItem
        v-for="tweet in drafts"
        :key="tweet.id"
        :tweet="tweet"
        isDraft
      />
    </div>
  </div>
</template>

<script>
import TweetItem from "./TweetItem.vue";
export default {
  components: { TweetItem },
  props: {
    tweets: { type: Array, required: true, default: () => [] },
    drafts: { type: Array, required: true, default: () => [] },
  },
};
</script>

<style>
</style>