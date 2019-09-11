<template>
  <v-app>
    <v-app-bar elevation="0" height="80" fixed app>
      <!-- 로고: #e04034 -->
      <!-- 배경: #a7d22b -->
      <v-toolbar-title class="display-1 font-weight-bold ml-10" v-text="title" />
      <v-spacer></v-spacer>
      <v-toolbar-items class="mr-10 hidden-sm-and-down">
        <v-btn
          v-for="item in items"
          :key="item.title"
          class="headline font-weight-light"
          text
          @click="$router.push({ path: item.to })"
        >{{ item.title }}</v-btn>
      </v-toolbar-items>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" x-large class="mr-8 hidden-md-and-up"></v-app-bar-nav-icon>
      <v-navigation-drawer v-model="drawer" app disable-resize-watcher right>
        <v-list>
          <v-list-item
            v-for="item in items"
            :key="item.title"
            @click="$router.push({ path: item.to })"
          >
            <v-list-item-content>
              <v-list-item-title class="headline font-weight-light">{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
    </v-app-bar>
    <v-content>
      <v-container class="ma-0 pa-0" fluid>
        <nuxt />
      </v-container>
    </v-content>
    <!-- PC -->
    <v-footer :fixed="fixed" height="80" app class="px-12 hidden-xs-and-down">
      <div>
        <span>주소: {{ address }}</span>
        <br />
        <span>전화번호: {{ telNum }}</span>
        <span class="ml-4">이메일: {{ companyEmail }}</span>
      </div>
      <v-spacer></v-spacer>
      <div>&copy; {{ new Date().getFullYear() }} GMK. All rights reserved.</div>
    </v-footer>
    <!-- 모바일 -->
    <v-footer :fixed="fixed" height="80" app class="px-10 hidden-sm-and-up">
      <div class="caption">
        <span>주소: {{ address }}</span>
        <br />
        <span>전화번호: {{ telNum }}</span>
        <span class="ml-4">이메일: {{ companyEmail }}</span>
        <br />
        <span>&copy; {{ new Date().getFullYear() }} GMK. All rights reserved.</span>
      </div>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      fixed: false,
      items: [
        {
          title: '홈',
          to: '/'
        },
        {
          title: '회사소개',
          to: '/about'
        },
        {
          title: '제품정보',
          to: '/products'
        },
        {
          title: '부품정보',
          to: '/wareparts'
        },
        {
          title: '연락처',
          to: '/contact'
        }
      ],
      title: 'GMK',
      address: '충청남도 아산시 음봉면 월산로 253-7',
      telNum: '041-532-3924',
      companyEmail: 'gmk6309@gmail.com'
    }
  }
}
</script>