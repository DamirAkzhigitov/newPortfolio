<template>
  <section class="description">
    <div class="description__status">
      <div class="description__status-icon">
        {{ availability }}
      </div>
    </div>
    <div v-if="ready" class="description__text animate__animated animate__fadeInLeft">
      <p v-for="(paragraph, index) in description" :key="index">
        {{ paragraph }}
      </p>
    </div>
  </section>
</template>

<script lang="ts">
import { computed, PropType, ref, watch } from 'vue'
import { AboutMeBlockItem } from '@/models/api'

export default {
  props: {
    value: {
      type: Array as PropType<AboutMeBlockItem>,
      default() {
        return []
      }
    },
    animation: {
      type: Boolean,
      default: false
    }
  },
  setup(props) {
    console.log('setup props: ', props)
    const ready = ref(false)

    const description = computed(() => {
      const list = props.value?.description?.L

      if (list) {
        return list
          .map((item) => item.M)
          .sort((a, b) => a.order.N - b.order.N)
          .map(({ text }) => text.S)
      }

      return []
    })

    const availability = computed(() => {
      const available = props.value?.availability?.BOOL

      return available ? 'Available' : 'Not available'
    })

    watch(
      () => props.animation,
      (val) => {
        if (typeof val === 'boolean') {
          ready.value = val
        }
      }
    )

    return {
      description,
      availability,
      ready
    }
  }
}
</script>

<style lang="scss">
.description__text {
  p {
    margin-top: 10px;
  }
}
</style>
