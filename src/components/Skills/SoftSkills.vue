<template>
  <section class="skills__soft-skills">
    <ul class="soft-skills">
      <li
        v-for="softSkill in softSkills"
        :key="softSkill.key"
        class="soft-skill"
      >
        <div class="soft-skill__content">
          <span>{{ softSkill.title }}</span>
        </div>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  name: "SoftSkills",

  data() {
    return {
      softSkills: [
        {
          key: "teamwork",
          title: "Teamwork",
        },
        {
          key: "responsibility",
          title: "Responsibility",
        },
        {
          key: "self-motivation",
          title: "Self-Motivation",
        },
        {
          key: "decisiveness",
          title: "Decisiveness",
        },
        {
          key: "time-management",
          title: "Time Management",
        },
        {
          key: "problem-solving",
          title: "Problem Solving",
        },
        {
          key: "communication",
          title: "Communication",
        },
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/styles/constants.scss";

.skills__soft-skills {
  .soft-skills {
    list-style: none;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    padding: 20px 10px 0;

    .soft-skill {
      position: relative;
      width: 150px;
      height: 150px;
      margin: 0 40px 20px;
      padding: 3px;
      @include transition(0.3s);

      &::before {
        position: absolute;
        content: "";
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        z-index: -1;
        background: $primaryGradientColor;
        border-radius: 50%;
        @include transform(scale(0));
        @include transition(0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275));
      }

      @media screen and (max-width: 576px) {
        width: 120px;
        height: 120px;
        margin: 0 20px 20px;

        .soft-skill__content {
          span {
            font-size: 10px !important;
          }
        }
      }

      &:hover {
        &:nth-child(odd) {
          @include transform(scale(1.3) rotateY(360deg));
        }

        &:nth-child(even) {
          @include transform(scale(1.3) rotate(360deg));
        }

        &::before {
          @include transform(scale(1));
        }
      }

      .soft-skill__content {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        height: 100%;
        background: #fff;
        border-radius: 50%;
        box-shadow: 0 10px 30px 0 rgba(0, 0, 0, 0.15);

        span {
          text-transform: uppercase;
          color: $primaryColor;
          font-size: 12px;
          letter-spacing: 0.5px;
        }
      }
    }
  }
}
</style>