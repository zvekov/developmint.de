<template>
  <div>
    <div class="h-48 bg-rains" />
    <section class="flex flex-col flex-wrap items-center bg-gray-lighter py-8 leading-normal text-gray-darkest">
      <!-- eslint-disable-next-line vue/no-v-html -->
      <div class="justify-around items-center w-5/6 md:w-1/2 mx-auto legal" v-html="$t('legal.privacy')" />
    </section>
  </div>
</template>

<script>
export default {
  head () {
    return {
      ...this.$t('seo.privacy'),
      meta: [
        { hid: 'robots', name: 'robots', content: 'noindex' }
      ]
    }
  },
  watch: {
    '$route' (to, from) {
      if (to.hash === '#optout') {
        this.optOut()
      }
    }
  },
  methods: {
    optOut () {
      document.cookie = 'ga_optout=true; expires=Thu, 31 Dec 2099 23:59:59 UTC; path=/'
      this.$ga.disable()
    }
  }
}
</script>

<style lang="postcss">
  .legal > h1 {
    @apply font-bold text-2xl
  }
  .legal > h2 {
    @apply font-bold text-xl
  }
  .legal > h3 {
    @apply font-bold text-lg
  }
  .legal > a {
    @apply underline text-blue-400;

    &:hover {
      @apply text-indigo-400
    }
  }
  .legal > ul {
    @apply list-disc px-8
  }
</style>
