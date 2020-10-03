<template>
  <section id="hobbies">
    <b-container>
      <b-card v-for="hobbie in hobbies" :key="hobbie.key">
        <img :src="hobbie.image" />
        <h1>{{ hobbie.title }}</h1>
      </b-card>
    </b-container>
  </section>
</template>

<script>
export default {
  name: "Hobbies",

  data() {
    return {
      hobbies: [
        {
          key: "music",
          title: "Music",
          image: require("@/assets/music.jpg"),
        },
        {
          key: "travel",
          title: "Travel",
          image: require("@/assets/travel.jpg"),
        },
        {
          key: "foods",
          title: "Foods",
          image: require("@/assets/foods.jpg"),
        },
        {
          key: "meet-friends",
          title: "Meet Friends",
          image: require("@/assets/meet-friends.jpg"),
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/styles/constants.scss";

#hobbies {
  min-height: 100vh;
  display: flex;
  align-items: center;
  padding: 80px 0;

  .container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;

    .card {
      position: relative;
      width: 300px;
      height: 300px;
      margin: 40px;
      border: none;
      box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
      border-radius: 8px;
      overflow: hidden;

      @media screen and (max-width: 992px) {
        margin-right: 10px;
        margin-left: 10px;
      }

      @media screen and (max-width: 350px) {
        width: 200px;
        height: 200px;
        margin-right: 0;
        margin-left: 0;
      }

      &::before {
        position: absolute;
        content: "";
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        background: $primaryGradientColor;
        opacity: 0;
        z-index: 1;
        @include transition(0.3s);
      }

      &:hover {
        &::before {
          opacity: 0.7;
        }

        .card-body {
          img {
            @include transform(scale(1.1));
          }

          h1 {
            opacity: 2;
          }
        }
      }

      .card-body {
        padding: 0;

        img {
          width: 100%;
          @include transition(0.3s);
        }

        h1 {
          position: absolute;
          top: 50%;
          left: 50%;
          opacity: 0;
          z-index: 1;
          color: #fff;
          letter-spacing: 1.5px;
          text-shadow: 2px 4px 3px rgba(0, 0, 0, 0.3);
          @include transform(translate(-50%, -50%));
        }
      }
    }
  }
}
</style>