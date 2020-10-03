<template>
  <header :class="{ fixed: this.isFixed }">
    <b-container>
      <span @click="scrollToTop">NTD</span>

      <b-nav>
        <b-nav-item
          v-for="item in mainMenu"
          :key="item.key"
          exact
          :class="{ active: item.key === itemMenuActive }"
          @click="() => scrollToSection(item.key)"
          >{{ item.title }}</b-nav-item
        >
      </b-nav>
    </b-container>
  </header>
</template>

<script>
export default {
  name: "HeaderNavbar",

  data() {
    return {
      mainMenu: [
        {
          key: "info",
          title: "About",
        },
        {
          key: "summary",
          title: "Summary",
        },
        {
          key: "skills",
          title: "Skills",
        },
        {
          key: "experiences",
          title: "Experiences",
        },
        {
          key: "hobbies",
          title: "Hobbies",
        },
      ],
      navHided: false,
      navExpanded: false,
      isFixed: false,
      itemMenuActive: "info",
    };
  },

  computed: {
    activeMenu() {
      const key = this.$route.matched[0].meta;
      return key ? [key] : [];
    },
  },

  mounted() {
    this.addEventWindowOnResize();
    this.checkIsMobile();
    this.fixHeaderWhenScrollDown();
    this.activateCurrentItemMenu();
  },

  methods: {
    addEventWindowOnResize() {
      window.addEventListener("resize", (e) => {
        if (e.target.innerWidth <= 576) {
          this.navHided = true;
        } else {
          this.navHided = false;
          this.navExpanded = false;
        }
      });
    },

    checkIsMobile() {
      this.navExpanded = false;
      const windowWidth = window.innerWidth;
      this.navHided = windowWidth <= 576;
    },

    onToggleClick() {
      this.navExpanded = !this.navExpanded;

      if (this.navExpanded) {
        document.body.classList.add("overflow-hidden");
      } else {
        document.body.classList.remove("overflow-hidden");
      }
    },

    fixHeaderWhenScrollDown() {
      window.addEventListener("scroll", () => {
        if (window.pageYOffset > 100) this.isFixed = true;
        else this.isFixed = false;
      });
    },

    scrollToTop() {
      window.scrollTo({ top: 0 });
    },

    activateCurrentItemMenu() {
      window.addEventListener("scroll", () => {
        const windowTop = window.pageYOffset + window.innerHeight;
        const aboutTop = document.getElementById("info").offsetTop;
        const summaryTop = document.getElementById("summary").offsetTop;
        const skillsTop = document.getElementById("skills").offsetTop;
        const experiencesTop = document.getElementById("experiences").offsetTop;
        const hobbiesTop = document.getElementById("hobbies").offsetTop;

        if (windowTop >= hobbiesTop) {
          this.itemMenuActive = "hobbies";
        } else if (windowTop >= experiencesTop) {
          this.itemMenuActive = "experiences";
        } else if (windowTop >= skillsTop) {
          this.itemMenuActive = "skills";
        } else if (windowTop >= summaryTop) {
          this.itemMenuActive = "summary";
        } else if (windowTop >= aboutTop) {
          this.itemMenuActive = "info";
        } else {
          this.itemMenuActive = null;
        }
      });
    },

    scrollToSection(sectionId) {
      const section = document.getElementById(sectionId);
      window.scrollTo({ top: section.offsetTop - 20 });
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/styles/constants.scss";

header {
  position: absolute;
  width: 100%;
  padding: 20px 0;
  background: transparent;
  z-index: 9999;

  &.fixed {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    padding: 5px 0;
    background: $primaryGradientColor;
    box-shadow: 0 0 5px 5px rgba(0, 0, 0, 0.1);
    @include animation(header-motion 0.5s);
  }

  .container {
    display: flex;
    justify-content: space-between;
    align-items: center;

    @media screen and (max-width: 786px) {
      justify-content: center;
    }

    span {
      position: relative;
      color: #fff;
      font-size: 25px;
      font-weight: 800;
      letter-spacing: 30px;
      margin-right: -30px;
      cursor: pointer;

      &::before,
      &::after {
        position: absolute;
        content: "";
        width: 20px;
        height: 2px;
        background: #fff;
        top: 50%;
        @include transform(translateY(-50%));
      }

      &::before {
        left: 22px;
      }

      &::after {
        right: 51px;
      }
    }

    .nav {
      @media screen and (max-width: 786px) {
        position: fixed;
        right: 10px;
        top: 50%;
        @include transform(translateY(-50%));

        flex-direction: column;
        background: $primaryGradientColor;
        border-radius: 4px;
        box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
        padding: 5px;

        .nav-item {
          .nav-link {
            margin-right: 0 !important;
            font-size: 12px !important;
            padding: 5px;
          }
        }
      }

      .nav-item {
        &:last-child {
          .nav-link {
            margin-right: 0;
          }
        }

        &.active {
          .nav-link {
            color: #000;

            &::before {
              @include transform(scale(1));
            }
          }
        }

        .nav-link {
          position: relative;
          color: #fff;
          font-size: 14px;
          font-weight: 500;
          margin-right: 10px;

          &::before {
            position: absolute;
            content: "";
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            background: #fff;
            border-radius: 4px;
            z-index: -1;
            @include transition(0.3s);
            @include transform(scale(0));
          }

          &:hover {
            color: #000;

            &::before {
              @include transform(scale(1));
            }
          }

          &.router-link-active {
            background: #fff;
            color: #000;
            border-radius: 4px;
          }
        }
      }
    }
  }
}

@keyframes header-motion {
  0% {
    @include transform(translateY(-200%));
  }
  100% {
    @include transform(translateY(0));
  }
}
</style>