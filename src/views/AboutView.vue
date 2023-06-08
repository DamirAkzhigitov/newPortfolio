<template>
  <div class='about-page'>
    <avatar-info class='avatar-info' />
    <short-description class='short-description' />
    <experience-list class='experience-list' />
    <contact-block class='contact-block'/>
    <education-block class='education-block'/>
    <projects-description class='projects-description' />
    <skills-list class='skills-list'/>
  </div>
</template>

<script setup lang='ts'>
import { defineAsyncComponent } from 'vue'

const EducationBlock  = defineAsyncComponent(() => import("@/components/AboutView/EducationBlock.vue"))
const ContactBlock = defineAsyncComponent(() => import("@/components/AboutView/ContactBlock.vue"))
const AvatarInfo = defineAsyncComponent(() => import("@/components/AboutView/AvatarInfo.vue"))
const ProjectsDescription = defineAsyncComponent(() => import("@/components/AboutView/ProjectsDescription.vue"))
const SkillsList = defineAsyncComponent(() => import("@/components/AboutView/SkillsList.vue"))
const ShortDescription = defineAsyncComponent(() => import("@/components/AboutView/ShortDescription.vue"))
const ExperienceList = defineAsyncComponent(() => import("@/components/AboutView/ExperienceList.vue"))
</script>

<style lang='scss'>
.about-page {
  display: grid;
  grid-template-columns: 60% 1fr;
  grid-template-rows: repeat(5, auto);
  grid-gap: 5px;
  max-width: 1024px;
  margin: 40px auto 0;

  .avatar-info,
  .projects-description,
  .skills-list {
    grid-column: 1/3;
  }

  & > section {
    padding: 10px;
    border: 1px solid;
  }
}
</style>