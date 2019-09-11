<template>
  <v-layout column justify-center class="mx-12">
    <v-flex xs12 sm8 md6>
      <br />
      <div class="display-2 grey--text font-weight-light">부품정보</div>
      <br />
      <v-tabs grow height="60" color="#e04034" show-arrows>
        <v-tab v-for="item in items" :key="item.tabName" class="mx-0">{{ item.tabName }}</v-tab>
        <v-tab-item v-for="tabItem in items" :key="tabItem.tabName">
          <v-card flat>
            <v-card-text>
              <div>
                <span class="display-3 font-weight-light">{{ tabItem.tabName }}</span>
              </div>
            </v-card-text>
            <v-container fluid class="pa-0">
              <v-row>
                <v-col sm="12" lg="12" class="pa-0">
                  <v-card class="ma-4">
                    <v-card-title>
                      <div class="flex-grow-1"></div>
                      <v-text-field v-model="search" label="Search" single-line hide-details></v-text-field>
                    </v-card-title>

                    <v-data-table
                      :headers="headers"
                      :items="tabItem.contents"
                      :search="search"
                      class="elevation-0"
                    >
                      <template v-slot:item.photo="{ item }">
                        <v-img
                          :src="getImage(tabItem.tabName, item.photo)"
                          max-height="100"
                          max-width="100"
                        ></v-img>
                      </template>
                    </v-data-table>
                  </v-card>
                </v-col>
              </v-row>
            </v-container>
          </v-card>
        </v-tab-item>
      </v-tabs>
    </v-flex>
  </v-layout>
</template>

<script>
import mitsubishi from '../static/mitsubishi.json'
import sodick from '../static/sodick.json'
import fanuc from '../static/fanuc.json'
import makino from '../static/makino.json'
import seibu from '../static/seibu.json'
import brother from '../static/brother.json'
import hitachi from '../static/hitachi.json'
import japax from '../static/japax.json'
import charmailes from '../static/charmailes.json'
import agie from '../static/agie.json'
import spm from '../static/spm.json'
import chmer from '../static/chmer.json'
import ona from '../static/ona.json'
import accutex from '../static/accutex.json'
import avng from '../static/avng.json'
import belt from '../static/belt.json'
import jig from '../static/jig.json'
import etc from '../static/etc.json'

export default {
  data() {
    return {
      search: '',
      headers: [
        { text: 'Photo', value: 'photo' },
        { text: 'Item No.', value: 'itemNum' },
        { text: 'O / Part No.', value: 'partNum' },
        { text: 'Size (mm)', value: 'size' },
        { text: 'Product Name', value: 'name' },
        { text: 'Position / Type', value: 'position' },
        { text: 'Description', value: 'description' }
      ],
      items: [
        {
          tabName: 'Mitsubishi',
          jsonFile: mitsubishi,
          contents: []
        },
        {
          tabName: 'Sodick',
          jsonFile: sodick,
          contents: []
        },
        {
          tabName: 'Fanuc',
          jsonFile: fanuc,
          contents: []
        },
        {
          tabName: 'Makino',
          jsonFile: makino,
          contents: []
        },
        {
          tabName: 'Seibu',
          jsonFile: seibu,
          contents: []
        },
        {
          tabName: 'Brother',
          jsonFile: brother,
          contents: []
        },
        {
          tabName: 'Hitachi',
          jsonFile: hitachi,
          contents: []
        },
        {
          tabName: 'Japax',
          jsonFile: japax,
          contents: []
        },
        {
          tabName: 'Charmailes',
          jsonFile: charmailes,
          contents: []
        },
        {
          tabName: 'Agie',
          jsonFile: agie,
          contents: []
        },
        {
          tabName: 'SPM',
          jsonFile: spm,
          contents: []
        },
        {
          tabName: 'CHMER',
          jsonFile: chmer,
          contents: []
        },
        {
          tabName: 'ONA',
          jsonFile: ona,
          contents: []
        },
        {
          tabName: 'Accutex',
          jsonFile: accutex,
          contents: []
        },
        {
          tabName: 'AV&G',
          jsonFile: avng,
          contents: []
        },
        {
          tabName: 'Belt',
          jsonFile: belt,
          contents: []
        },
        {
          tabName: 'JIG',
          jsonFile: jig,
          contents: []
        },
        {
          tabName: 'etc',
          jsonFile: etc,
          contents: []
        }
      ]
    }
  },
  created() {
    this.loadData
  },
  computed: {
    loadData() {
      this.items.forEach(item => {
        item.jsonFile.forEach(e => {
          var newContent = {
            photo: e.photo,
            itemNum: e.itemNum,
            partNum: e.partNum,
            size: e.size,
            name: e.name,
            position: e.position,
            description: e.description
          }

          item.contents.push(newContent)
        })
      })
    }
  },
  methods: {
    getImage(tabName, photo) {
      return '../' + tabName.toLowerCase() + '/' + photo
    }
  }
}
</script>