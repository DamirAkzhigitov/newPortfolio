<template>
  <section class="avatar-container">
    <ul class="avatar-soft-skill items-end">
      <li v-for="skill in skillsLeft" :key="skill" class="avatar-soft-skill__item text-nowrap">
        <div v-show="skill.loading" class="item-title v-skeleton-loader__bone"></div>
        <div v-show="!skill.loading">
          <img :src="skill?.icon" class="item-icon" />
          <span class="item-title">{{ skill?.title }}</span>
        </div>
      </li>
    </ul>
    <div class="profile-container d-flex justify-center items-center flex-column">
      <figure class="profile-picture__container">
        <img src="/Pic.png" class="profile-picture__image" alt="" />
        <figcaption class="profile-picture__tag text-bold-large text-nowrap">
          Frontend Engineer
        </figcaption>
      </figure>
      <div class="profile__name text-bold-large">Damir Akzhigitov</div>
      <div class="profile__location">Limassol, Cyprus</div>
    </div>
    <ul class="avatar-soft-skill items-end">
      <li v-for="skill in skillsRight" :key="skill" class="avatar-soft-skill__item text-nowrap">
        <div v-show="skill.loading" class="item-title v-skeleton-loader__bone"></div>
        <div v-show="!skill.loading">
          <img :src="skill?.icon" class="item-icon" />
          <span class="item-title">{{ skill?.title }}</span>
        </div>
      </li>
    </ul>
    <div class="avatar-hard-skills items-start">
      <div
        v-for="skill in hardSkills"
        :key="skill.alt"
        class="avatar-hard-skills__item"
        :style="`background-color: ${skill.color}`"
      >
        <img :src="skill.icon" height="24" width="24" class="hard-skills__logo" />
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

const format = (str) => str.toLowerCase().replace(/[^a-zA-Z\d|&]/g, '_')

const getIcon = (name) => `/logos/${name}.svg`

const loading = ref(true)

const loadingsSkills = [
  {
    loading: true
  },
  {
    loading: true
  },
  {
    loading: true
  }
]

const skillsLeft = ref(loadingsSkills)
const skillsRight = ref(loadingsSkills)

const hardSkills = ref([
  {
    icon: '/logos/git.svg',
    alt: 'git',
    color: 'rgba(240, 60, 46, 0.1);'
  }
])

const getSkills = async () => {
  const data = await fetch('/api/skills')

  const response = await data.json()

  if (Array.isArray(response) && response.length > 0) {
    const skillsResponse = response[0]

    const { SS: skillList } = skillsResponse.skills

    const rightSide = skillList.map((item) => {
      const iconName = format(item)

      return {
        title: item,
        icon: getIcon(iconName)
      }
    })

    skillsLeft.value = rightSide.splice(0, 3)
    skillsRight.value = rightSide

    // loading.value = false
    console.log('skillsLeft: ', skillsLeft.value)
  }
}

onMounted(() => {
  getSkills()
})
</script>

<style lang="scss">
$shadow: 5px 5px 35px -15px rgba(0, 0, 0, 0.2);

.avatar-container {
  display: grid;
  grid-template-rows: 1fr 60px;
  grid-template-columns: 1fr 1fr 1fr;
  grid-gap: 15px;

  max-width: 700px;
  width: 100%;
  margin: 0 auto;

  .profile-container {
    box-shadow: $shadow;
    border-radius: var(--space-m);
    padding: var(--space-m);

    .profile-picture {
      &__image {
        height: 180px;
        width: auto;
      }
      &__container {
        position: relative;
        height: 150px;
      }
      &__tag {
        position: absolute;
        bottom: 0;
        right: 50%;
        transform: translate(50%, -50%);
        background: linear-gradient(135deg, #26cbff 0%, #1b67d9 64.06%, #0f44ff 100%);
        box-shadow: 0 5px 20px rgba(250, 118, 96, 0.2);
        border-radius: var(--space-xs);
        text-align: center;
        color: #ffffff;
        padding: 0 var(--space-xs);
      }
    }

    @media screen and (max-width: 600px) {
      .profile-picture__image {
        height: 140px;
      }
    }
  }

  .avatar-soft-skill {
    display: flex;
    flex-flow: column;
    justify-content: center;
    align-items: center;
    padding: 0;
    font-family: 'JetBrains Mono', monospace;
    user-select: none;

    .item-icon {
      width: 20px;
      height: 20px;
      margin-right: var(--space-s);
    }
    &__item {
      width: fit-content;
      padding: var(--space-sm) var(--space-m);
      display: flex;
      align-items: center;
      box-shadow: $shadow;
      transition: all 0.5s ease-out;

      border-radius: var(--space-xs);
      margin: var(--space-s);

      background-color: #fff;

      &:hover {
        box-shadow: 5px 5px 35px -15px rgba(0, 0, 0, 0.5);
      }
    }
    .item-title.v-skeleton-loader__bone {
      width: 100px;
      height: 20px;
    }

    @media screen and (max-width: 600px) {
      .avatar-soft-skill__item {
        box-shadow: 5px 5px 25px -5px rgba(0, 0, 0, 0.22);
      }
      .item-title {
        display: none;
      }
      .item-icon {
        margin-right: 0;
      }
    }
  }

  .avatar-hard-skills {
    grid-column: 1/4;

    &__item {
      width: 60px;
      height: 60px;
      background: #f4eefb;
      border-radius: 40%;
      display: flex;
      align-items: center;
      justify-content: center;
    }
  }
}
</style>
