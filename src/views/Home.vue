<template>
  <section class="home">
    <info />
    <about />
    <skills />
    <experiences />
    <hobbies />
  </section>
</template>

<script>
import Info from "@/components/Info";
import About from "@/components/Summary";
import Skills from "@/components/Skills/index";
import Experiences from "@/components/Experiences";
import Hobbies from "@/components/Hobbies";

export default {
  name: "Home",

  components: {
    Info,
    About,
    Skills,
    Experiences,
    Hobbies,
  },

  metaInfo: {
    title: "NTD Portfolio",
  },
};
</script>
