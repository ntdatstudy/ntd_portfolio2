<template>
  <div>
    <header-navbar />

    <main>
      <router-view />
    </main>
  </div>
</template>

<script>
import HeaderNavbar from "@/components/HeaderNavbar";

export default {
  name: "MasterLayout",

  components: {
    HeaderNavbar,
  },

  data() {
    return {
      isLoading: true,
    };
  },

  mounted() {
    setTimeout(() => {
      this.isLoading = false;
    }, 1000);
  },
};
</script>
