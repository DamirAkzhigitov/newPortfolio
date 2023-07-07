<template>
  <div class="about-page">
    <avatar-info class="avatar-info" />
    <short-description class="short-description" />
    <contact-block class="contact-block" />
    <experience-list class="experience-list" />
    <education-block class="education-block" />
    <projects-description class="projects-description" />
    <skills-list class="skills-list" />
  </div>
</template>

<script setup lang="ts">
import { defineAsyncComponent, onMounted } from 'vue'

const API = 'https://6h68rbyn3i.execute-api.eu-north-1.amazonaws.com/dev'

const EducationBlock = defineAsyncComponent(
  () => import('@/components/AboutView/EducationBlock.vue')
)
const ContactBlock = defineAsyncComponent(() => import('@/components/AboutView/ContactBlock.vue'))
const AvatarInfo = defineAsyncComponent(() => import('@/components/AboutView/AvatarInfo.vue'))
const ProjectsDescription = defineAsyncComponent(
  () => import('@/components/AboutView/ProjectsDescription.vue')
)
const SkillsList = defineAsyncComponent(() => import('@/components/AboutView/SkillsList.vue'))
const ShortDescription = defineAsyncComponent(
  () => import('@/components/AboutView/ShortDescription.vue')
)
const ExperienceList = defineAsyncComponent(
  () => import('@/components/AboutView/ExperienceList.vue')
)

const callApi = () => {
  // instantiate a headers object
  const myHeaders = new Headers()
  // add content type header to object
  myHeaders.append('Content-Type', 'application/json')
  // using built in JSON utility package turn object to string and store in a variable
  const raw = JSON.stringify({
    firstName: 'Damir',
    lastName: 'Testov'
  })
  // create a JSON object with parameters for API call and store in a variable
  const requestOptions: RequestInit = {
    method: 'POST',
    headers: myHeaders,
    body: raw,
    redirect: 'follow'
  }
  // make API call with parameters and use promises to get response
  fetch(API, requestOptions)
    .then((response) => response.text())
    .then((result) => alert(JSON.parse(result).body))
    .catch((error) => console.log('error', error))
}

onMounted(() => {
  // callApi()
})
</script>

<style lang="scss">
.about-page {
  display: grid;
  grid-template-columns: 60% 1fr;
  grid-template-rows: repeat(5, auto);
  grid-gap: var(--space-xs);
  max-width: 1024px;
  margin: var(--space-l) auto 0;

  .avatar-info,
  .projects-description,
  .skills-list {
    grid-column: 1/3;
  }

  & > section {
    padding: var(--space-s);
  }

  @media screen and (max-width: 600px) {
    display: flex;
    flex-flow: column;
  }
}
</style>
