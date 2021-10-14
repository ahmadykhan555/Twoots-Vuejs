
<template>
  <div>
    <form class="flex flex-col" action="" @submit.prevent="handleNewTweet">
      <textarea
        class="p-4 border-2 mb-2 bg-white rounded-md"
        name="new-tweet"
        id="new-tweet"
        cols="30"
        rows="4"
        v-model="content"
      ></textarea>
      <select
        class="bg-white p-2"
        name="select-type"
        id="select-type"
        v-model="type"
      >
        <option v-for="type in tweetTypes" :key="type" :value="type.value">
          {{ type.displayValue }}
        </option>
      </select>
      <button
        class="
          border-2 border-green-400
          bg-green-500
          text-white
          font-bold
          uppercase
          rounded-md
          p-2
          mt-2
        "
      >
        Tweet!!
      </button>
    </form>
  </div>
</template>

<script>
export default {
  data: () => ({
    tweetTypes: [
      {
        value: "draft",
        displayValue: "Draft",
      },
      {
        value: "instant",
        displayValue: "Instant Tweet",
      },
    ],
    content: "",
    type: "instant",
  }),
  methods: {
    handleNewTweet() {
      this.$emit("createNewTweet", {
        content: this.content,
        type: this.type,
      });
    },
  },
};
</script>

<style>
</style>