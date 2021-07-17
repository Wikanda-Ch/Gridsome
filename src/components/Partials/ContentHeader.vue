<template>
  <div >
    <div class="z-100 text-center py-10 md:py-20" v-if="!hasImage">
      <h2 v-if="title!=null" class="h1 font-extrabold dark:text-gray-400">{{ title }}</h2>
      <p v-if="sub!=null" class="text-gray-600 text-light font-sans">{{ sub }}</p>
    </div>

    <div v-if="hasImage" class="z-100 relative mt-0 h-auto">
      <g-image
        v-if="hasImage && staticImage"
        :src="require(`!!assets-loader!@pageImage/${image}`)"
        width="1400"
        height="400"
        class="object-cover absolute -z-10 h-full w-full"
      ></g-image>

      <g-image
        v-if="hasImage && !staticImage"
        :src="image"
        width="1400"
        height="400"
        class="object-cover absolute -z-10 h-full w-full"
      ></g-image>

      <slot>
        <div style="color:#93cbff; text-shadow: 2px -1px white"
          class="text-center bg-gray-800 lg:py-48 md:py-32 py-24"
          :class='`bg-opacity-0`'
        >
          <h2 v-if="title!=null" class="h1 font-extrabold" style="font-family: 'Kanit', sans-serif;">{{ title }}</h2>
          <p v-if="sub!=null" class="h5 font-sans" style="font-family: 'Kanit', sans-serif;">{{ sub }}</p>
        </div>
      </slot>
    </div>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Kanit:wght@200;400&display=swap');
</style>

<script>
export default {
  props: {
    title: {
      type: String,
      default: null
    },
    sub: {
      type: String,
      default: null
    },
    image: {
      type: String | Object,
      default: null
    },
    staticImage: {
      type: Boolean,
      default: true
    },
    opacity: {
      type: Number,
      default: 50
    }
  },
  computed: {
    hasImage() {
      return this.image ? true : false;
    }
  }
};
</script>

<style>
</style>