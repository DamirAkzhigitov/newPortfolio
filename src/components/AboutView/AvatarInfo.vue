<template>
  <section class="avatar-container">
    <ul class="avatar-soft-skill items-end">
      <li v-for="skill in skillsLeft" :key="skill" class="avatar-soft-skill__item text-nowrap">
        <img :src="skill.icon" class="item-icon" />
        <span class="item-title">{{ skill.title }}</span>
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
    <ul class="avatar-soft-skill">
      <li v-for="skill in skillsRight" :key="skill" class="avatar-soft-skill__item text-nowrap">
        <img :src="skill.icon" class="item-icon" />
        <span class="item-title">{{ skill.title }}</span>
      </li>
    </ul>
    <div class="avatar-hard-skills items-start">
      <div class="avatar-hard-skills__item">
        <img src="/logos/figma-logo.png" class="hard-skills__logo" />
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const skillsLeft = ref([
  {
    icon: '/logos/javascript.svg',
    title: 'Javascript'
  },
  {
    icon: '/logos/aws-amplify.svg',
    title: 'AWS amplify'
  },
  {
    icon: '/logos/vuetify.svg',
    title: 'Vuetify'
  }
])
const skillsRight = ref([
  {
    icon: '/logos/html.svg',
    title: 'HTML 5'
  },
  {
    icon: '/logos/network-connection.svg',
    title: 'GraphQL & REST'
  },
  {
    icon: '/logos/scss.svg',
    title: 'Sass'
  }
])
</script>

<style lang="scss">
$shadow: 5px 5px 35px -15px rgba(0, 0, 0, 0.2);

.avatar-container {
  display: grid;
  grid-template-rows: 1fr 60px;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 15px;

  max-width: 700px;
  width: 100%;
  margin: 0 auto;

  .profile-container {
    box-shadow: $shadow;
    border-radius: var(--space-m);
    padding: var(--space-m);
    min-width: 250px;

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
  }

  .avatar-soft-skill {
    display: flex;
    flex-flow: column;
    justify-content: center;
    padding: 0;
    font-family: 'JetBrains Mono', monospace;
    user-select: none;

    .item-icon {
      width: 20px;
      height: 20px;
      margin-right: var(--space-s);
    }
    &__item {
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
