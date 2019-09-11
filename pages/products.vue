<template>
  <v-layout column justify-center class="mx-12">
    <v-flex xs12 sm8 md6>
      <br />
      <div class="display-2 grey--text font-weight-light">제품정보</div>
      <br />
      <v-tabs grow height="60" color="#e04034">
        <v-tab v-for="item in items" :key="item.tabName" class="subtitle-1 mx-0">
          {{ item.tabNameKor }}
          ({{ item.tabNameEng }})
        </v-tab>
        <v-tab-item v-for="item in items" :key="item.tabName">
          <v-card flat>
            <v-img :src="item.parallaxImg" height="400"></v-img>
            <br />
            <v-card-text>
              <div>
                <span class="display-3 font-weight-medium">{{ item.tabNameEng }}</span>
                <span class="display-3 font-weight-light mx-4">|</span>
                <span class="display-2 font-weight-light">{{ item.tabNameKor }}</span>
              </div>
            </v-card-text>

            <v-card-text class="headline black--text">{{ item.tabDescription }}</v-card-text>
            <br />
            <v-container fluid class="pa-0">
              <v-row>
                <v-col v-for="card in item.table" :key="card.title" sm="12" lg="6" class="pa-0">
                  <v-card class="ma-4" v-if="card.headers">
                    <v-card-title>
                      <span class="display-1">{{ card.title }}</span>
                    </v-card-title>
                    <br />
                    <v-data-table
                      :headers="card.headers"
                      :items="card.contents"
                      class="elevation-0"
                      hide-default-footer
                      disable-sort
                    ></v-data-table>
                  </v-card>

                  <v-card class="ma-4" v-else>
                    <v-card-title>
                      <span class="display-1">{{ card.title }}</span>
                      <v-spacer></v-spacer>
                      <span class="headline">{{ card.titleSub }}</span>
                    </v-card-title>
                    <br />
                    <v-img :src="card.img" max-height="300" contain></v-img>
                    <v-card-text class="title">{{ card.description }}</v-card-text>
                    <v-simple-table>
                      <tbody>
                        <tr v-for="infomation in card.infomations" :key="infomation.name">
                          <td class="font-weight-medium">{{ infomation.name }}</td>
                          <td>{{ infomation.value }}</td>
                        </tr>
                      </tbody>
                    </v-simple-table>
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
export default {
  data() {
    return {
      items: [
        {
          tabNameKor: '황동 와이어',
          tabNameEng: 'Brass Wire',
          parallaxImg: '../wire_main4.jpg',
          tabDescription:
            'GMK가 제공하는 와이어 컷팅의 기본인 황동 와이어는 각 고객의 특성에 맞게 원재료 성분이 CuZn37과 CuZn40으로 나뉘어져 있습니다. 태선기, 중선기 등 모든 생산라인은 철저한 규격에 의한 자동화 시스템을 갖추고 있으며 수치 설정에 의한 자동제어방식으로 규격과 품질이 보장된 최고의 Brass Wire 중선을 생산하고 있습니다. EDM Wire를 비롯하여 안테나, 커넥터, 각종 볼트 및 너트의 원자재로 사용되고 있으며, 고도의 정밀도를 요구하는 기계, 전자, 자동차 등 다양한 산업의 설비용 부품소재로도 사용되고 있습니다.',
          table: [
            {
              title: 'Cut-S',
              titleSub: 'Standard EDM Brass: CuZn37',
              img: '../cut-s.jpg',
              description:
                '표준 황동와이어인 Cut-S는 동과 아연의 구성비율이 63:37이고, 940 N/mm² 이상인 인장강도를 가지고 있습니다. 단일구조의 동과 아연의 합금으로 구성된 표준 방전가공용 전극선으로서 비용대비 탁월한 성능을 보임은 물론 일반적인 가공환경에도 두루 적합한 황동와이어 입니다. 우수한 진직도를 바탕으로 와이어의 구동방식에 상관없이 탁월한 자동결선 성능을 자랑하며, 와이어표면처리도 깔끔하여 파우더 발생 문제를 해결한 제품입니다.',
              infomations: [
                {
                  name: 'diameter',
                  value: '0.10 - 0.33 mm'
                },
                {
                  name: 'tolerance',
                  value: '+0mm, -0.002 mm'
                },
                {
                  name: 'tensileStrHard',
                  value: 'Over 940 N/mm²'
                },
                {
                  name: 'tensileStrSoft',
                  value: '460 - 520 N/mm²'
                },
                {
                  name: 'conductivity',
                  value: '21%'
                }
              ]
            },
            {
              title: 'Cut-H',
              titleSub: 'High Zinc Alloyed Brass: CuZn40',
              img: '../cut-h.jpg',
              description:
                '고농도 아연 합금 황동 와이어인 CUT-H는 동과 아연의 구성비율이 60:40이고, 1,000 N/mm² 이상인 인장강도를 가지고 있습니다. 표준 황동 와이어에 비해 가공속도가 빠르고 높은 정밀도를 요구하는 작업에 적합합니다. 탁월한 진직도를 바탕으로 와이어의 구동방식에 상관없이 탁월한 자동결선 성능을 자랑하며, 와이어표면처리도 깔끔하여 파우더 발생 문제를 해결한 제품입니다.',
              infomations: [
                {
                  name: 'diameter',
                  value: '0.10 - 0.33 mm'
                },
                {
                  name: 'tolerance',
                  value: '+0mm, -0.002 mm'
                },
                {
                  name: 'tensileStrHard',
                  value: 'Over 1000 N/mm²'
                },
                {
                  name: 'tensileStrSoft',
                  value: '460 - 520 N/mm²'
                },
                {
                  name: 'conductivity',
                  value: '23%'
                }
              ]
            }
          ]
        },
        {
          tabNameKor: '도금 와이어',
          tabNameEng: 'Coated Wire',
          parallaxImg: '../wire_main3.jpg',
          tabDescription:
            'GMK가 제공하는 다양한 종류의 도금 와이어들은 정밀 면조도를 요구하는 고속가공에 적합하게 설계되어 있습니다. 기존 아연 도금와이어들이 가지고 있는 치명적인 가루발생을 감소시킨 제품입니다. 기존의 자사 아연 도금 와이어들은 작업중 가루발생의 원인이 되는 불안정한 도금표층의 문제로부터 자유로울 수가 없었으나, 다양한 고객의 요구에 대응 할 수 있게 독특한 도금방법으로 설계된 GMK의 도금와이어 제품들은 안정적인 표면을 구축하게 되어 기존의 가루발생 문제를 최소화 시키는데 성공하였습니다. 아울러 GMK의 모든 아연 도금와이어는 타사제품들과 다르게 납(Pb)을 전혀 사용하지 않은 친환경 제품입니다.',
          table: [
            {
              title: 'Cut-Z',
              titleSub: 'Various Cutting Purpose',
              img: '../cut-z.jpg',
              description:
                'CUT-Z는 가장 일반적으로 다양한 가공 조건에 사용할 수 있는 범용 도금와이어입니다. 1차 가공시 다양한 가공조건에서도 CUT-S 대비 20-30% 향상된 가공속도를 나타내며, 안정된 전도성과 파우더 발생방지를 보장하는 탁월한 제품입니다.',
              infomations: [
                {
                  name: 'diameter',
                  value: '0.10 - 0.33 mm'
                },
                {
                  name: 'tolerance',
                  value: '+0mm, -0.002 mm'
                },
                {
                  name: 'tensileStrHard',
                  value: 'Over 930 N/mm²'
                },
                {
                  name: 'tensileStrSoft',
                  value: '450 - 510 N/mm²'
                },
                {
                  name: 'conductivity',
                  value: '22%'
                }
              ]
            },
            {
              title: 'Cut-ZA',
              titleSub: 'High Accurate Cutting',
              img: '../cut-za.jpg',
              description:
                'CUT-ZA는 여타 아연코팅 와이어에 비해 정밀한 면조도를 요구하는 초정밀가공에 적합한 와이어입니다. 안정된 전도성과 파우더 발생방지를 보장하는 탁월한 제품입니다. 특히 AGIE(아지) 기종에서 탁월한 성능을 나타냅니다.',
              infomations: [
                {
                  name: 'diameter',
                  value: '0.10 - 0.33 mm'
                },
                {
                  name: 'tolerance',
                  value: '+0mm, -0.002 mm'
                },
                {
                  name: 'tensileStrHard',
                  value: 'Over 930 N/mm²'
                },
                {
                  name: 'tensileStrSoft',
                  value: '450 - 510 N/mm²'
                },
                {
                  name: 'conductivity',
                  value: '19%'
                }
              ]
            },
            {
              title: 'Cut-ZS',
              titleSub: 'High Speed & Accurate Cutting',
              img: '../cut-zs.jpg',
              description:
                'Cut-ZS는 여타 아연코팅 와이어에 비해 빠른 가공 속도와 정밀한 면조도를 요구하는 고속정밀 가공에 적합한 와이어입니다. 코어와 도금부분의 접착력을 탁월하게 향상시킨 제품으로 가루발생 가능성을 대폭 줄였습니다. 도금부 표층이 균일한 결정립으로 구성이 되어있으며 이것이 바로 안정적인 방전의 핵심입니다.',
              infomations: [
                {
                  name: 'diameter',
                  value: '0.10 - 0.33 mm'
                },
                {
                  name: 'tolerance',
                  value: '+0mm, -0.002 mm'
                },
                {
                  name: 'tensileStrHard',
                  value: 'Over 930 N/mm²'
                },
                {
                  name: 'tensileStrSoft',
                  value: '450 - 510 N/mm²'
                },
                {
                  name: 'conductivity',
                  value: '20%'
                }
              ]
            },
            {
              title: 'Cut-X',
              titleSub: 'High Speed Cutting',
              img: '../cut-x.jpg',
              description:
                'Cut-X는 기계 부품 등 고속가공용의 수요가 점차 늘어나고 있는 소비자의 요구에 맞추어 개발한 제품으로, 99.99%의 순동으로 코어로 구성되어있어 테퍼 가공이 가능합니다. 표층에 두꺼운 고농도 아연 층을 가지고 있어 고속 및 정밀가공에 적합한 전통적인 타입입니다.',
              infomations: [
                {
                  name: 'diameter',
                  value: '0.25 - 0.33 mm'
                },
                {
                  name: 'tolerance',
                  value: '+0mm, -0.002 mm'
                },
                {
                  name: 'tensileStr',
                  value: 'Over 490 N/mm²'
                },
                {
                  name: 'conductivity',
                  value: '81%'
                }
              ]
            }
          ]
        },
        {
          tabNameKor: '전극관',
          tabNameEng: 'Pipe electrode',
          parallaxImg: '../pipe_electrode.jpg',
          tabDescription:
            'GMK의 철저한 품질관리 하에 생산된 전극관은 싱글과 멀티에 관계없이 정확한 내경과 외경을 유지 하고 있으며 진직도 역시 매우 뛰어 납니다. 아울러 다양한 홀 가공에서 매우 뛰어난 작업성과 경제성으로 고객 여러분들을 만족시켜 드릴 것 입니다.',
          table: [
            {
              title: 'Product Range',
              headers: [
                {
                  text: 'Type',
                  align: 'left',
                  sortable: false,
                  value: 'name'
                },
                { text: 'Material', value: 'material' },
                { text: 'Description', value: 'description' },
                { text: 'Length', value: 'length' }
              ],
              contents: [
                {
                  name: 'Single',
                  material: 'Copper',
                  description: '0.15mm to 25.00mm',
                  length: '200mm - 400mm'
                },
                {
                  name: 'Single',
                  material: 'Brass',
                  description: '0.15mm to 6.00mm',
                  length: '200mm - 470mm'
                },
                {
                  name: 'Japanese(SL)',
                  material: 'Copper',
                  description: '0.40mm to 3.00mm',
                  length: '200mm - 400mm'
                },
                {
                  name: 'Japanese(SL)',
                  material: 'Brass',
                  description: '0.40mm to 3.00mm',
                  length: '200mm - 400mm'
                },
                {
                  name: 'Multi-channel',
                  material: 'Copper',
                  description: '0.50mm to 25.00mm',
                  length: '200mm - 400mm'
                },
                {
                  name: 'Multi-channel',
                  material: 'Brass',
                  description: '0.50mm to 6.00mm',
                  length: '200mm - 400mm'
                },
                {
                  name: 'Pole',
                  material: 'Copper',
                  description: '1.00mm to 3.00mm',
                  length: '200mm - 400mm'
                }
              ]
            }
          ]
        }
      ]
    }
  }
}
</script>