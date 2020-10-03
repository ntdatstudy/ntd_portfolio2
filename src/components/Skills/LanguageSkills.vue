<template>
  <section class="skills__languages">
    <ul class="languages">
      <li v-for="language in languages" :key="language.key" class="language">
        <div class="language__content">
          <div class="language__logo">
            <img :src="language.logo" />
          </div>
          <span class="language__title">{{ language.title }}</span>
        </div>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  name: "LanguageSkills",

  data() {
    return {
      languages: [
        {
          key: "html",
          title: "HTML",
          logo: require("@/assets/html-logo.png"),
        },
        {
          key: "css",
          title: "CSS",
          logo: require("@/assets/css-logo.png"),
        },
        {
          key: "js",
          title: "Javascript",
          logo: require("@/assets/js-logo.png"),
        },
        {
          key: "php",
          title: "PHP",
          logo: require("@/assets/php-logo.png"),
        },
        {
          key: "sql-server",
          title: "Microsoft SQL Server",
          logo: require("@/assets/sql-server-logo.png"),
        },
        {
          key: "mysql",
          title: "MySQL",
          logo: require("@/assets/mysql-logo.png"),
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/styles/constants.scss";

.skills__languages {
  .languages {
    list-style: none;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    padding: 20px 10px 0;

    .language {
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
        @include transition(0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275));
      }

      &:hover {
        z-index: 999;
        @include transform(translateY(-25px) scale(1.2));

        &::before {
          @include transform(scale(1));
        }

        .language__content {
          .language__logo {
            // @include animation(logo-motion 0.5s);
            @include transform(rotate(360deg));
          }
        }
      }

      .language__content {
        display: flex;
        justify-content: flex-start;
        align-items: center;
        flex-direction: column;
        width: 100%;
        height: 100%;
        background: #fff;
        border-radius: 8px;

        .language__logo {
          display: flex;
          justify-content: center;
          align-items: center;
          width: 150px;
          height: 150px;
          margin: 10px 0;

          border-radius: 50%;
          background: #fff;
          @include transition(0.5s);

          @media screen and (max-width: 576px) {
            width: 80px;
            height: 80px;
          }

          img {
            width: 60%;
          }
        }

        .language__title {
          font-weight: 600;
        }
      }
    }
  }
}

@keyframes logo-motion {
  0% {
    @include transform(rotate(0deg));
  }
  100% {
    @include transform(rotate(360deg));
  }
}
</style>