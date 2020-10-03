<template>
  <section id="summary">
    <b-container>
      <div class="summary__bg">
        <h1>Summary</h1>
        <p v-if="!isDesktop">
          A random paragraph can also be an excellent way for a writer to tackle
          writers' block. Writing block can often happen due to being stuck with
          a current project that the writer is trying to complete. By inserting
          a completely random paragraph from which to begin, it can take down
          some of the issues that may have been causing the writers' block in
          the first place.
        </p>
      </div>
      <div v-if="isDesktop" class="summary__content">
        <p>
          A random paragraph can also be an excellent way for a writer to tackle
          writers' block. Writing block can often happen due to being stuck with
          a current project that the writer is trying to complete. By inserting
          a completely random paragraph from which to begin, it can take down
          some of the issues that may have been causing the writers' block in
          the first place.
        </p>
      </div>
    </b-container>
  </section>
</template>

<script>
export default {
  name: "Summary",

  data() {
    return {
      isDesktopScreen: false,
    };
  },

  computed: {
    isDesktop() {
      return this.isDesktopScreen || window.innerWidth >= 992;
    },
  },

  mounted() {
    this.addEventWindowOnResize();
  },

  methods: {
    addEventWindowOnResize() {
      window.addEventListener("resize", () => {
        this.isDesktopScreen = window.innerWidth >= 992;
      });
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/styles/constants.scss";

#summary {
  min-height: 100vh;
  display: flex;
  align-items: center;
  // margin-bottom: 100px;

  .container {
    display: flex;
    justify-content: space-between;
    align-items: center;

    .summary__bg {
      position: relative;
      width: 400px;
      height: 400px;
      background: $primaryGradientColor;
      // background: url("../assets/summary-bg.jpg") no-repeat center center;
      // background-size: cover;
      border-radius: 8px;

      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;

      @media screen and (max-width: 992px) {
        width: 100%;
        height: auto;
        padding: 40px 100px;

        p {
          margin-bottom: 0;
          margin-top: 20px;

          color: #fff;
          font-weight: 500;
          font-size: 14px;
          text-align: justify;
        }
      }

      @media screen and (max-width: 786px) {
        padding-left: 30px;
        padding-right: 30px;
      }

      h1 {
        color: #fff;
        letter-spacing: 5px;
        text-shadow: 0 0 5px rgba(0, 0, 0, 0.4);
        margin-bottom: 0;
      }
    }

    .summary__content {
      width: 50%;

      p {
        color: $primaryColor;
        text-align: justify;
        font-size: 20px;
        font-weight: 300;
      }
    }
  }
}
</style>