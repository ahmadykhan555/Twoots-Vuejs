<template>
  <nav
    class="
      w-full
      h-14
      py-4
      px-10
      bg-pink-500
      flex
      justify-between
      fixed
      top-0
      left-0
    "
  >
    <p class="text-white font-black text-xl">Twitter</p>
    <p class="text-gray-50 font-bold text-lg">@ _username</p>
  </nav>
  <div class="w-full mt-14">
    <UserProfile />
  </div>
</template>

<script>
import UserProfile from "./components/UserProfile.vue";
export default {
  name: "App",
  components: { UserProfile },
};
</script>

<style>
@tailwind base;
@tailwind components;
@tailwind utilities;
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background: #2c3e501a;
}
</style>
