<script setup lang="ts">
import { computed } from 'vue'

// inherited attrs can mess up the satori parser
defineOptions({
  inheritAttrs: false
})

const props = defineProps({
  path: String,
  title: {
    type: String,
    default: 'Og Image Template'
  },
  description: {
    type: String,
    default: 'Set a description to change me.'
  },
  background: {
    type: String,
    default: 'linear-gradient(to bottom, #dbf4ff, #fff1f1)'
  },
  color: {
    type: String
  },
  padding: {
    type: String,
    default: '0 50px'
  },
  titleFontSize: {
    type: String,
    default: '50px'
  },
  descriptionFontSize: {
    type: String,
    default: '35px'
  },
  icon: {
    type: [String, Boolean],
    default: 'logos:nuxt'
  },
  image: {
    type: String,
    required: false
  },
  siteName: {
    type: String,
    required: false
  },
  siteLogo: {
    type: String,
    required: false
  }
})

const backgroundAttrs = computed(() => {
  // we want to make a
  // const isBackgroundTw = props.background?.startsWith('bg-')
  return {
    style: {
      display: 'flex',
      position: 'absolute',
      width: '100%',
      height: '100%',
      background: 'rgba(51, 132, 173, 1)'
    }
  }
})

const backgroundFlareAttrs = computed(() => {
  // we want to make a
  // const isBackgroundTw = props.background?.startsWith('bg-')
  return {
    style: {
      display: 'flex',
      position: 'absolute',
      left: '-50%',
      bottom: '-10%',
      width: '200%',
      height: '200%',
      backgroundImage: 'radial-gradient(circle, rgba(178, 209, 224, 0.2) 0%, rgba(127, 178, 203, 0.8) 50%, rgba(51, 132, 173, 0) 70%)'
    }
  }
})

const backgroundFlareTwoAttrs = computed(() => {
  // we want to make a
  // const isBackgroundTw = props.background?.startsWith('bg-')
  return {
    style: {
      display: 'flex',
      position: 'absolute',
      right: '-30%',
      top: '-40%',
      width: '150%',
      height: '150%',
      backgroundImage: 'radial-gradient(circle, rgba(178, 209, 224, 0.8) 0%, rgba(127, 178, 203, 0.6) 50%, rgba(51, 132, 173, 0.3) 70%)'
    }
  }
})

const titleAttrs = computed(() => {
  const classes = []
  const styles = {
    fontWeight: 'bold',
    marginBottom: '50px',
    lineHeight: '70px',
    fontSize: props.titleFontSize
  }
  return { class: classes, style: styles }
})

const siteConfig = useSiteConfig()
const siteName = computed(() => {
  return props.siteName || siteConfig.name
})
const siteLogo = computed(() => {
  return props.siteLogo || siteConfig.logo || 'https://nuxt.com/assets/design-kit/logo/full-logo-green-light.png'
})
</script>

<template>
  <div v-bind="backgroundAttrs" />
  <div v-bind="backgroundFlareAttrs" />
  <div v-bind="backgroundFlareTwoAttrs" />
  <div class="w-full flex flex-row z-10">
    <div
      class="w-2/5"
      style="padding: 50px;"
    >
      <div class="flex flex-col h-full justify-between text-gray-100">
        <div class="flex flex-row justify-between items-center">
          <div class="flex flex-col">
            <div v-bind="titleAttrs">
              {{ title || 'Null Title' }}
            </div>
            <div
              v-if="'description'"
              class="text-2xl text-justify"
            >
              {{ description }}
            </div>
          </div>
        </div>
        <div class="text-white w-full flex flex-row">
          <img
            v-if="siteLogo"
            :src="siteLogo"
            height="53"
            class="rounded mr-2"
          >
          <div
            style="font-size: 34px;"
            class="font-bold mt-2"
          >
            {{ siteName }}
          </div>
        </div>
      </div>
    </div>
    <div class="w-3/5 h-full items-end">
      <img
        v-if="image"
        :src="`https://res.cloudinary.com/dyvpecjfg/image/upload/c_fill,h_960,w_1080/f_auto,q_auto:best,dpr_auto/${image}`"
        width="540"
        height="480"
        class="rounded-xl cursor-pointer shadow-lg m-auto"
      >
    </div>
  </div>
</template>
