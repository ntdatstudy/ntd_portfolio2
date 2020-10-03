<template>
  <section class="skills__frameworks">
    <ul class="frameworks">
      <li
        v-for="framework in frameworks"
        :key="framework.key"
        class="framework"
      >
        <div class="framework__content">
          <div class="logo-container">
            <div class="logo">
              <img :src="framework.logo" />
            </div>
          </div>
          <span class="title">{{ framework.title }}</span>
        </div>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  name: "FrameworkSkills",

  data() {
    return {
      frameworks: [
        {
          key: "oop",
          title: "OOP",
          logo: require("@/assets/oop-logo.png"),
        },
        {
          key: "laravel",
          title: "Laravel",
          logo: require("@/assets/laravel-logo.png"),
        },
        {
          key: "jquery",
          title: "JQuery",
          logo: require("@/assets/jquery-logo.png"),
        },
        {
          key: "vuejs",
          title: "VueJS",
          logo: require("@/assets/vuejs-logo.png"),
        },
        {
          key: "reactjs",
          title: "ReactJS",
          logo: require("@/assets/reactjs-logo.png"),
        },
        {
          key: "nodejs",
          title: "NodeJS",
          logo: require("@/assets/nodejs-logo.png"),
        },
        {
          key: "bootstrap",
          title: "Bootstrap",
          logo: require("@/assets/bootstrap-logo.png"),
        },
        {
          key: "ant-design",
          title: "Ant Design",
          logo: require("@/assets/antdesign-logo.png"),
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/styles/constants.scss";

.skills__frameworks {
  .frameworks {
    list-style: none;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    padding: 20px 10px 0;

    .framework {
      position: relative;
      width: 200px;
      height: 250px;
      margin: 0 10px 20px;
      padding: 5px;

      box-shadow: 0 10px 30px 0 rgba(0, 0, 0, 0.15);
      border-radius: 8px;
      @include transition(0.5s);

      @media screen and (max-width: 576px) {
        width: 130px;
        height: 200px;
      }

      &::before {
        position: absolute;
        content: "";
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;

        background: $primaryGradientColor;
        border-radius: 8px;
        z-index: -1;
        @include transform(scale(0));
        @include transition(0.3s);
      }

      &:hover {
        z-index: 999;
        @include transform(translateY(-25px) scale(1.2));

        &::before {
          @include transform(scale(1));
        }

        .framework__content {
          .logo-container {
            @include transform(translateY(-50px) rotateY(360deg));
          }
        }
      }

      .framework__content {
        display: flex;
        justify-content: flex-start;
        align-items: center;
        flex-direction: column;
        width: 100%;
        height: 100%;

        background: #fff;
        border-radius: 8px;

        .logo-container {
          position: relative;
          margin: 10px 0 30px;
          padding: 3px;
          @include transition(0.5s);

          &::before {
            position: absolute;
            content: "";
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            z-index: -1;

            background: $primaryGradientColor;
            border-radius: 8px;
          }

          .logo {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 130px;
            height: 130px;

            background: #fff;
            border-radius: 8px;

            @media screen and (max-width: 576px) {
              width: 80px;
              height: 80px;
            }

            img {
              width: 60%;
            }
          }
        }

        .title {
          font-weight: 600;
        }
      }
    }
  }
}
</style>