<template>
  <div>
    <div id="gantt_here" style='width:100%; height:100vh;'></div>
  </div>
</template>

<script>
/* eslint-disable */
import { gantt } from 'dhtmlx-gantt'
import 'dhtmlx-gantt/codebase/dhtmlxgantt.css';

export default {
  data () {
    return {
      data: [
        { id: 1, text: "사람에 대한 100가지 사실", start_date:"01-04-2018", duration: 18, progress:0.4, open:true },
        { id: 2, text: "사람은 어떻게 보는가", start_date:"02-04-2018", duration: 8, progress:0.6, parent:1 },
        { id: 3, text: "패턴인식", start_date:"11-04-2018", duration: 8, progress:0.6, parent:2 },
        { id: 4, text: "문화의 다름", start_date:"11-04-2018", duration: 8, progress:0.6, parent:2 },
        { id: 5, text: "상상 혹은 각도상", start_date:"11-04-2018", duration: 8, progress:0.6, parent:2 },
        { id: 6, text: "사람은 어떻게 읽는가", start_date:"11-04-2018", duration: 8, progress:0.6, parent:1 },
        { id: 7, text: "서체의 크기", start_date:"11-04-2018", duration: 8, progress:0.6, parent:6 },
        { id: 8, text: "긴 문장", start_date:"11-04-2018", duration: 8, progress:0.6, parent:6 },
        { id: 9, text: "읽기와 독해의 차이", start_date:"11-04-2018", duration: 8, progress:0.6, parent:6 },
        { id: 10, text: "사람은 어떻게 기억하는가", start_date:"11-04-2018", duration: 8, progress:0.6, parent:1 },
        { id: 11, text: "단기 기억력의 한계", start_date:"11-04-2018", duration: 8, progress:0.6, parent:10 },
        { id: 12, text: "정신적 자원의 필요", start_date:"11-04-2018", duration: 8, progress:0.6, parent:10 },
        { id: 13, text: "최대 4가지의 기억", start_date:"11-04-2018", duration: 8, progress:0.6, parent:10 },
        { id: 14, text: "정보의 인식", start_date:"11-04-2018", duration: 8, progress:0.6, parent:10 },
        { id: 15, text: "사람은 어떻게 생각하는가", start_date:"11-04-2018", duration: 8, progress:0.6, parent:1 },
        { id: 16, text: "사고방식", start_date:"11-04-2018", duration: 8, progress:0.6, parent:15 },
        { id: 17, text: "몰입상태", start_date:"11-04-2018", duration: 8, progress:0.6, parent:15 },
        { id: 18, text: "상대적 시간", start_date:"11-04-2018", duration: 8, progress:0.6, parent:15 },
        { id: 19, text: "예제를 통한 학습", start_date:"11-04-2018", duration: 8, progress:0.6, parent:15 },
        { id: 20, text: "사람은 어떻게 주의를 집중하는가", start_date:"11-04-2018", duration: 8, progress:0.6, parent:1 },
        { id: 21, text: "주목은 선택적", start_date:"11-04-2018", duration: 8, progress:0.6, parent:1 },
      ],
      links: [
        { id: 1, source:1, target:2, type:"1" },
        { id: 2, source:2, target:3, type:"0" }
      ]
    }
  },
  created () {
    //
  },
  mounted () {
    gantt.init('gantt_here')  // 간트 그리기
    gantt.parse({ data: this.data, links: this.links });  // 간트 내 데이터 삽입
  }
}
</script>

<style scoped>
</style>
