<template>
  <section id="experiences">
    <b-container
      class="experiences__content"
      :class="{ disabled: companyActive }"
    >
      <div v-for="company in companies" :key="company.key" class="company">
        <aside>
          <span>{{ company.startDate }}</span>
          <span>-</span>
          <span>{{ company.endDate }}</span>
        </aside>
        <article>
          <div class="logo">
            <img :src="company.logo" />
          </div>
          <div class="info">
            <h1>{{ company.title }}</h1>
            <b-button @click="seeDetails(company.key)">See details</b-button>
          </div>
        </article>
      </div>
    </b-container>
    <section class="details__content">
      <template v-for="company in companies">
        <article
          v-for="project in company.projects"
          :key="project.key"
          :class="{ active: companyActive === company.key }"
        >
          <h1>{{ project.title }}</h1>
          <div class="info">
            <label>Position:</label>
            <p>{{ project.position }}</p>
          </div>
          <div class="info">
            <label>Position:</label>
            <p>{{ project.position }}</p>
          </div>
          <div class="info">
            <label>Description:</label>
            <p>{{ project.description }}</p>
          </div>
          <div class="info">
            <label>Team Size:</label>
            <p>{{ project.teamSize }}</p>
          </div>
          <div class="info">
            <label>Technologies:</label>
            <p>{{ project.technologies }}</p>
          </div>
          <b-button @click="closeDetails">
            <a-icon type="close" />
          </b-button>
        </article>
      </template>
    </section>
  </section>
</template>

<script>
export default {
  name: "Experiences",

  data() {
    return {
      companies: [
        {
          key: "tma-solutions",
          title: "TMA Solutions",
          logo: require("@/assets/tma-solutions-logo.png"),
          startDate: "Jul 2019",
          endDate: "Apr 2020",
          projects: [
            {
              key: "suretraxx",
              title: "SureTraxx",
              position: "Fullstack Developer",
              description:
                "A system handles digital cash management programs and tools for retailers, banks, and armored carriers.",
              teamSize: "8-12",
              technologies: "Laravel Framework, MySQL",
            },
          ],
        },
        {
          key: "silicon-stack",
          title: "Silicon Stack",
          logo: require("@/assets/silicon-stack-logo.png"),
          startDate: "Jul 2020",
          endDate: "Now",
          projects: [
            {
              key: "kraftheinz",
              title: "KraftHeinz",
              position: "Frontend Developer",
              description:
                "A system manage export & import goods, production process and customers.",
              teamSize: "20-25",
              technologies: "VueJS Framework, .NET Core, Microsoft SQL Server",
            },
          ],
        },
      ],
      companyActive: null,
    };
  },

  methods: {
    seeDetails(companyKey) {
      this.companyActive = companyKey;
      document.body.classList.add("overflow-hidden");
    },

    closeDetails() {
      this.companyActive = null;
      document.body.classList.remove("overflow-hidden");
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/styles/constants.scss";

#experiences {
  display: flex;
  align-items: center;
  min-height: 100vh;
  background: $primaryGradientColor;

  .experiences__content {
    position: relative;
    max-width: 700px;
    padding-top: 30px;
    padding-bottom: 30px;

    @media screen and (max-width: 576px) {
      &::before {
        content: none !important;
      }
    }

    &::before {
      position: absolute;
      content: "";
      width: 10px;
      left: 50px;
      top: 20px;
      bottom: 20px;
      background: rgba(0, 0, 0, 0.2);
      border-radius: 10px;
    }

    &.disabled {
      pointer-events: none;
    }

    .company {
      position: relative;
      margin: 20px 0 20px 130px;
      padding: 20px 60px;

      background: #fff;
      border-radius: 8px;
      box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
      @include transition(0.3s);

      @media screen and (max-width: 768px) {
        padding: 20px;
      }

      @media screen and (max-width: 576px) {
        margin-left: 0;
        margin-top: 130px;
      }

      &::before {
        position: absolute;
        content: "";
        // box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;

        @media screen and (min-width: 576px) {
          border-right: 10px solid #fff;
          border-top: 10px solid transparent;
          border-bottom: 10px solid transparent;
          top: 50%;
          left: -10px;
          @include transform(translateY(-50%));
        }

        @media screen and (max-width: 576px) {
          border-bottom: 10px solid #fff;
          border-left: 10px solid transparent;
          border-right: 10px solid transparent;
          top: 0;
          left: 50%;
          @include transform(translate(-50%, -100%));
        }
      }

      &:hover {
        @include transform(scale(0.9));

        aside {
          background: $primaryGradientColor;

          @media screen and (min-width: 576px) {
            left: -180px;
            @include transform(translateY(-50%) rotate(360deg) scale(1.1));
          }

          @media screen and (max-width: 576px) {
            @include transform(translateX(-50%) rotate(360deg) scale(1.1));
          }

          span {
            color: #fff;
            font-weight: 500;
            text-shadow: 2px 4px 3px rgba(0, 0, 0, 0.3);
          }
        }
      }

      aside {
        position: absolute;
        width: 95px;
        height: 95px;

        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;

        background: #fff;
        border: 3px solid #fff;
        border-radius: 50%;
        @include transition(0.3s);

        @media screen and (min-width: 576px) {
          top: 50%;
          left: -137px;
          @include transform(translateY(-50%));
        }

        @media screen and (max-width: 576px) {
          top: -110px;
          left: 50%;
          @include transform(translateX(-50%));
        }

        span {
          font-size: 13px;
          line-height: 1;
        }
      }

      article {
        display: flex;
        justify-content: space-between;
        align-items: center;

        @media screen and (max-width: 576px) {
          flex-direction: column;

          .logo {
            margin-bottom: 20px;
          }
        }

        .logo {
          img {
            height: 150px;
            border-radius: 8px;
          }
        }

        .info {
          h1 {
            font-size: 20px;
            font-weight: 300;
            letter-spacing: 1px;
          }

          button {
            position: relative;
            padding: 10px 30px;
            color: $primaryColor;
            font-size: 12px;
            border: none;
            background: #fff;
            outline: none;
            box-shadow: rgba(0, 0, 0, 0.16) 0px 3px 6px,
              rgba(0, 0, 0, 0.23) 0px 3px 6px;
            border-radius: 4px;
            overflow: hidden;
            z-index: 1;

            &:hover {
              color: #fff;
              text-shadow: 2px 4px 3px rgba(0, 0, 0, 0.3);

              &::before {
                @include transform(translateX(0));
              }
            }

            &::before {
              position: absolute;
              content: "";
              width: 100%;
              height: 100%;
              top: 0;
              left: 0;
              z-index: -1;
              background: $primaryGradientColor;

              @include transform(translateX(-100%));
              @include transition(0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94));
            }
          }
        }
      }
    }
  }

  .details__content {
    article {
      position: fixed;
      width: 550px;
      top: 50%;
      left: 50%;
      padding: 40px 20px 20px;
      z-index: 9999;
      overflow-y: auto;
      background: #fff;
      border-radius: 8px;
      box-shadow: rgba(17, 17, 26, 0.1) 0px 8px 24px,
        rgba(17, 17, 26, 0.1) 0px 16px 56px, rgba(17, 17, 26, 0.1) 0px 24px 80px;
      @include transition(0.3s);
      @include transform(translate(-50%, -50%) scale(0));

      @media screen and (max-width: 576px) {
        width: 95%;
      }

      &.active {
        @include transform(translate(-50%, -50%) scale(1));
      }

      h1 {
        font-size: 30px;
      }

      .info {
        label {
          font-weight: 500;
          margin-bottom: 2px;
        }
      }

      button {
        position: absolute;
        display: flex;
        padding: 10px;
        right: 10px;
        top: 10px;
      }
    }
  }
}
</style>