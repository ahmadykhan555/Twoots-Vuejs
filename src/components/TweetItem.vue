<template>
  <div
    :class="isDraft ? 'bg-red-50 ' : 'bg-green-50'"
    class="
      tweet-item
      mr-4
      mb-2
      border-b border-gray-300
      cursor-pointer
      p-6
      rounded-md
      w-8/12
      text-left
    "
    @click="markFavorite(tweet.id)"
  >
    <p>{{ tweet.content }}</p>
  </div>
</template>

<script>
export default {
  props: {
    tweet: { type: Object, default: () => ({}), required: true },
    isDraft: { type: Boolean, default: () => false },
  },
  methods: {
    markFavorite(id) {
      this.$emit("markFavorite", { id });
    },
  },
};
/**
 * emit => to trigger events from child
 */
</script>

<style>
</style>

