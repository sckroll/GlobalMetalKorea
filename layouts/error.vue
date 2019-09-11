<template>
  <v-app>
    <v-layout column justify-center align-center>
      <div v-if="error.statusCode === 404">
        <div class="display-2 text-center pa-1">{{ pageNotFound }}</div>
        <div
          class="display-1 grey--text font-weight-light text-center pa-1"
        >{{ pageNotFoundDesciption }}</div>
      </div>
      <div v-else>
        <div class="display-2 text-center pa-1">{{ otherError }}</div>
        <div
          class="display-1 grey--text font-weight-light text-center pa-1"
        >{{ otherErrorDesciption }}</div>
      </div>
      <v-btn
        class="headline font-weight-light ma-4"
        text
        tile
        @click="$router.push({ path: '/' })"
      >홈으로 돌아가기</v-btn>
    </v-layout>
  </v-app>
</template>

<script>
export default {
  layout: 'empty',
  props: {
    error: {
      type: Object,
      default: null
    }
  },
  head() {
    const title =
      this.error.statusCode === 404 ? this.pageNotFound : this.otherError
    return {
      title
    }
  },
  data() {
    return {
      pageNotFound: '404 Not Found',
      pageNotFoundDesciption: '올바른 페이지가 아닙니다',
      otherError: 'Error',
      otherErrorDesciption: '오류가 발생하였습니다'
    }
  }
}
</script>

<style scoped>
h1 {
  font-size: 20px;
}
</style>
