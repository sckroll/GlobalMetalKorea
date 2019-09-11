<template>
  <v-layout column justify-center class="mx-12">
    <v-flex xs12 sm8 md6>
      <br />
      <div class="display-2 grey--text font-weight-light">연락처</div>
      <br />
      <vue-daum-map
        :appKey="mapData.appKey"
        :center.sync="mapData.center"
        :level.sync="mapData.level"
        :mapTypeId="mapData.mapTypeId"
        :libraries="mapData.libraries"
        @load="onLoad"
        style="width:100%;height:400px;"
      ></vue-daum-map>
      <br />
      <div class="text-center">
        <span class="display-1">{{ address }}</span>
      </div>
      <br />
      <div>
        <v-container fluid class="pa-0">
          <v-row>
            <v-col sm="12" lg="6" class="pa-0">
              <v-card class="ma-4">
                <v-card-title primary-title class="font-weight-bold">GMK 연락처</v-card-title>
                <v-divider></v-divider>
                <v-card-text>
                  <div>
                    <span class="headline grey--text font-weight-light">전화번호</span>
                    <span class="headline black--text ml-6">{{ telNum }}</span>
                  </div>
                  <div>
                    <span class="headline grey--text font-weight-light">팩스</span>
                    <span class="headline black--text ml-6">{{ faxNum }}</span>
                  </div>
                  <div>
                    <span class="headline grey--text font-weight-light">이메일</span>
                    <span class="headline black--text ml-6">{{ companyEmail }}</span>
                  </div>
                </v-card-text>
              </v-card>
            </v-col>
            <v-col sm="12" lg="6" class="pa-0">
              <v-card class="ma-4">
                <v-card-title primary-title class="font-weight-bold">대표 연락처</v-card-title>
                <v-divider></v-divider>
                <v-card-text>
                  <div>
                    <span class="headline grey--text font-weight-light">대표자명</span>
                    <span class="headline black--text ml-6">{{ ceo }}</span>
                  </div>
                  <div>
                    <span class="headline grey--text font-weight-light">전화번호</span>
                    <span class="headline black--text ml-6">{{ hp }}</span>
                  </div>
                  <div>
                    <span class="headline grey--text font-weight-light">이메일</span>
                    <span class="headline black--text ml-6">{{ ceoEmail }}</span>
                  </div>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
import VueDaumMap from 'vue-daum-map'

export default {
  components: {
    VueDaumMap
  },
  data() {
    return {
      address: '충청남도 아산시 음봉면 월산로 253-7',
      telNum: '041-532-3924',
      faxNum: '041-532-3923',
      companyEmail: 'gmk6309@gmail.com',
      ceo: '김정석',
      hp: '010-8776-3924',
      ceoEmail: 'kjsuk021@hanmail.net',
      mapData: {
        appKey: '3805e0467c592210ffc76065f0a6b591',
        center: { lat: 33.450701, lng: 126.570667 },
        level: 3,
        mapTypeId: VueDaumMap.MapTypeId.NORMAL,
        libraries: ['services', 'clusterer', 'drawing'],
        map: null
      }
    }
  },
  methods: {
    // 지도가 로드 완료되면 load 이벤트 발생
    onLoad(map) {
      var kakaomaps = kakao.maps
      if (kakaomaps) {
        // 주소-좌표 변환 객체 생성
        var geocoder = new kakaomaps.services.Geocoder()

        // 주소로 좌표 검색
        geocoder.addressSearch(this.address, function(result, status) {
          if (status === kakaomaps.services.Status.OK) {
            var coords = new kakaomaps.LatLng(result[0].y, result[0].x)

            // 마커 생성 후 표시
            var marker = new kakaomaps.Marker({
              map: map,
              position: coords
            })
            marker.setMap(map)

            // 지도의 중심 설정
            map.setCenter(coords)

            // 지도타입 컨트롤 생성
            var mapTypeControl = new kakao.maps.MapTypeControl()
            map.addControl(mapTypeControl, kakao.maps.ControlPosition.TOPRIGHT)

            // 지도 줌 컨트롤 생성
            var zoomControl = new kakao.maps.ZoomControl()
            map.addControl(zoomControl, kakao.maps.ControlPosition.RIGHT)
          }
        })
        this.map = map
      }
    }
  }
}
</script>