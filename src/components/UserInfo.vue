<template>
  <div class="text-left user-profile-info p-4 bg-white rounded-md">
    <h3 class="items-start flex flex-col">
      <span class="flex-1 text-2xl">
        @{{ user.username }} - {{ user.fullName }}
      </span>
      <span
        v-if="user.isAdmin"
        class="
          w-auto
          rounded-lg
          text-white
          font-bold
          border-2 border-green-400
          px-2
          py-1
          text-xs
          bg-green-500
        "
        >Admin</span
      >
    </h3>
    <p class="my-3 text-xs">
      <strong>Followers: {{ followers }}</strong>
    </p>
    <button
      @click="followUser"
      class="
        border-2 border-green-600
        px-6
        py-1
        w-full
        rounded-lg
        text-xs text-green-900
        font-bold
      "
    >
      Follow
    </button>
  </div>
</template>

<script>
export default {
  props: {
    user: { type: Object, required: true },
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    },
  },
};
</script>

<style>
</style>