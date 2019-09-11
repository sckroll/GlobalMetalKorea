<template>
  <v-layout column justify-center class="mx-12">
    <v-flex xs12 sm8 md6>
      <br />
      <div class="display-2 grey--text font-weight-light">회사소개</div>
      <br />
      <v-parallax :src="parallaxImg">
        <v-row align="center" justify="center">
          <div class="text-center">
            <span class="display-3 font-weight-medium">{{ parallaxTitle }}</span>
            <br />
            <br />
            <span class="display-1 font-weight-light">{{ parallaxTitleSub }}</span>
          </div>
        </v-row>
      </v-parallax>
      <div class="text-center my-12" v-for="item in items" :key="item.title">
        <div class="display-2 font-weight-medium my-10">{{ item.title }}</div>
        <pre class="headline">{{ item.description }}</pre>
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data() {
    return {
      parallaxImg: '../wire_parallax.jpg',
      parallaxTitle: 'GLOBAL METAL KOREA, GMK',
      parallaxTitleSub: '세계적인 품질의 EDM 와이어를 만듭니다',
      items: [
        {
          title: 'WHO WE ARE',
          description:
            'GMK(Global Metal Korea)는 제조산업의 핵심영역인 금형가공에 필요한\n첨단기초소재인 EDM 와이어를 생산하는 기업입니다.'
        },
        {
          title: 'OUR VISION',
          description:
            '전기전자산업, 통신산업, 항공우주산업 등과 같은\n국가기간산업의 획기적인 발전에 기여하고픈 GMK는\n고객을 위한 정도ㆍ정품ㆍ정심 경영을 숭고한 목표로 세우고\n전 인류의 풍요로운 삶을 위해 헌신하는 기업,\n국가와 사회에 기여하는 책임 있는 기업으로서의 역할을 다하기 위해\n최선의 노력을 다하고 있습니다.'
        }
      ]
    }
  }
}
</script>