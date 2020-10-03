<template>
  <section id="skills">
    <a-tabs default-active-key="languages">
      <a-tab-pane key="languages" tab="Languages">
        <b-container>
          <language-skills />
        </b-container>
      </a-tab-pane>

      <a-tab-pane key="frameworks" tab="Frameworks">
        <b-container>
          <framework-skills />
        </b-container>
      </a-tab-pane>
      <a-tab-pane key="soft-skills" tab="Soft Skills">
        <b-container>
          <soft-skills />
        </b-container>
      </a-tab-pane>
    </a-tabs>
  </section>
</template>

<script>
import LanguageSkills from "./LanguageSkills";
import FrameworkSkills from "./FrameworkSkills";
import SoftSkills from "./SoftSkills";

export default {
  name: "Skills",

  components: {
    LanguageSkills,
    FrameworkSkills,
    SoftSkills,
  },
};
</script>

<style lang="scss" scoped>
@import "@/styles/constants.scss";

#skills {
  margin-bottom: 200px;

  ::v-deep {
    .ant-tabs {
      padding-top: 50px;

      .ant-tabs-bar {
        position: relative;
        border-bottom: 0;

        &::before {
          position: absolute;
          content: "";
          width: 100%;
          height: 2px;
          left: 0;
          bottom: 0;
          background: $primaryGradientColor;
        }

        .ant-tabs-nav-container .ant-tabs-nav-wrap .ant-tabs-nav {
          .ant-tabs-ink-bar {
            height: 100%;
            bottom: 3px;
            background: $primaryGradientColor;
            border-top-left-radius: 6px;
            border-top-right-radius: 6px;
          }

          .ant-tabs-tab {
            color: $primaryColor;
            font-weight: 500;
            font-size: 17px;

            &.ant-tabs-tab-active {
              color: #fff;
              z-index: 2;
            }
          }
        }
      }
    }
  }
}
</style>