<template>
  <section id="info">
    <div class="info__background" />

    <div class="info__details">
      <b-container>
        <b-container class="info__details-container">
          <b-row>
            <b-col class="avatar" lg="7">
              <img :src="developer.avatar" />
            </b-col>

            <b-col class="details" lg="5">
              <div class="details__section">
                <h6>Hello Everybody, I am</h6>
                <h3>{{ developer.name }}</h3>
                <!-- <h4>{{ developer.jobTitle }}</h4> -->
                <h4>??? Developer</h4>

                <p>
                  Don't talk, ACT.
                  <br />Don't say, SHOW. <br />Don't promise. PROVE.
                </p>

                <div class="about">
                  <!-- <div class="about__full-name">
                    <a-icon type="user" :style="aboutIconStyle" />
                    <span>{{ developer.fullName }}</span>
                  </div> -->

                  <div class="about__dob">
                    <a-icon type="calendar" :style="aboutIconStyle" />
                    <span>{{ developer.dob }}</span>
                  </div>

                  <div class="about__phone">
                    <a-icon type="phone" :style="aboutIconStyle" />
                    <span>{{ developer.phone }}</span>
                  </div>

                  <div class="about__address">
                    <a-icon type="home" :style="aboutIconStyle" />
                    <span>{{ developer.address }}</span>
                  </div>
                </div>

                <div class="contacts">
                  <a-tooltip
                    v-for="contact in contacts"
                    :key="contact.key"
                    placement="top"
                  >
                    <template #title>{{ contact.title }}</template>

                    <a
                      :class="`contacts__${contact.key}`"
                      :href="contact.link"
                      target="_blank"
                    >
                      <i :class="contact.icon" />
                    </a>
                  </a-tooltip>
                </div>

                <a-button type="primary" icon="cloud-download"
                  >DOWNLOAD MY CV</a-button
                >
              </div>
            </b-col>
          </b-row>
        </b-container>
      </b-container>
    </div>
  </section>
</template>

<script>
export default {
  name: "Info",

  data() {
    return {
      developer: {
        name: "Tan Dat Nguyen",
        // fullName: "Nguyen Tan Dat",
        avatar: require("../assets/avatar.jpg"),
        jobTitle: "Junior Frontend/PHP Developer",
        gender: "Male",
        dob: "March 16, 1998",
        phone: "0967 619 420",
        email: "tandatng163@gmail.com",
        address: "12 District, HCM City",
      },
      aboutIconStyle: {
        fontSize: "20px",
        color: "#766dff",
      },
      contacts: [
        {
          key: "gmail",
          title: "Gmail",
          icon: "fab fa-google",
          link: "https://www.gmail.com",
        },
        {
          key: "facebook",
          title: "Facebook",
          icon: "fab fa-facebook-f",
          link: "https://www.facebook.com/nguyendat163",
        },
        {
          key: "instagram",
          title: "Instagram",
          icon: "fab fa-instagram",
          link: "https://www.instagram.com/datielnguyen",
        },
        {
          key: "github",
          title: "Github",
          icon: "fab fa-github",
          link: "https://www.github.com",
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/styles/constants.scss";

#info {
  min-height: 100vh;
  position: relative;
  margin-bottom: 180px;

  @media screen and (max-width: 992px) {
    margin-bottom: 820px;
  }

  @media screen and (max-width: 768px) {
    margin-bottom: 730px;
  }

  @media screen and (max-width: 576px) {
    margin-bottom: 550px;
  }

  .info__background {
    height: 600px;
    background: $primaryGradientColor;
  }

  .info__details {
    position: absolute;
    top: 200px;
    width: 100%;

    @media screen and (max-width: 576px) {
      top: 100px;
    }

    .info__details-container {
      display: flex;
      justify-content: space-between;
      padding-top: 20px;
      padding-bottom: 20px;

      background: #fff;
      border-radius: 8px;
      box-shadow: 0px 20px 80px 0px rgba(153, 153, 153, 0.3);

      @media screen and (max-width: 380px) {
        justify-content: center;
      }

      .avatar {
        img {
          width: 100%;
          border-radius: 8px;
        }
      }

      .details {
        text-align: left;

        @media screen and (max-width: 992px) {
          text-align: center;
        }

        .details__section {
          padding: 50px 50px 0;

          h6 {
            font-size: 14px;
            letter-spacing: 2.1px;
            color: $primaryColor;
            text-transform: uppercase;
            font-weight: normal;
            margin-bottom: 13px;
          }

          h3 {
            font-size: 55px;
            font-weight: 800;
            text-transform: uppercase;
            margin-bottom: 0px;
          }

          h4 {
            font-size: 15px;
            font-weight: 500;
            text-transform: uppercase;
            margin-bottom: 40px;
          }

          p {
            font-size: 14px;
            color: $secondaryColor;
            margin-bottom: 40px;
          }

          .about {
            @media screen and (max-width: 992px) {
              display: flex;
              flex-direction: column;
              align-items: center;
            }

            [class^="about__"] {
              display: flex;
              align-items: center;
              margin-bottom: 15px;

              @media screen and (max-width: 992px) {
                flex-direction: column;
                margin-bottom: 10px;
              }

              i {
                margin-right: 15px;
              }

              span {
                color: $secondaryColor;
              }
            }
          }

          .contacts {
            display: flex;
            align-items: center;
            margin-top: 50px;

            @media screen and (max-width: 992px) {
              justify-content: center;
            }

            a {
              display: flex;
              align-items: center;
              justify-content: center;

              width: 40px;
              height: 40px;
              margin-right: 15px;

              background: #e8e8e8;
              border-radius: 4px;

              &:hover {
                background: $primaryGradientColor;
              }

              &:last-child {
                margin-right: 0;
              }

              i {
                color: #fff;
              }
            }
          }
        }

        .ant-btn {
          display: flex;
          align-items: center;
          line-height: normal;
          padding: 20px;
          background: $primaryGradientColor;
          font-size: 14px;
          border: none;

          @media screen and (min-width: 992px) {
            margin-top: 20px;
          }

          @media screen and (max-width: 992px) {
            margin: 20px auto 0;
          }
        }
      }
    }
  }
}
</style>