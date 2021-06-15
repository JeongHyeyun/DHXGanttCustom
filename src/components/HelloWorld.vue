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
        { id: 4, text: "Task #2", start_date:"11-04-2018", duration: 8, progress:0.6, parent:2 },
        { id: 5, text: "Task #2", start_date:"11-04-2018", duration: 8, progress:0.6, parent:2 },
        { id: 6, text: "사람은 어떻게 읽는가", start_date:"11-04-2018", duration: 8, progress:0.6, parent:1 },
        { id: 7, text: "Task #2", start_date:"11-04-2018", duration: 8, progress:0.6, parent:6 },
        { id: 8, text: "Task #2", start_date:"11-04-2018", duration: 8, progress:0.6, parent:6 },
        { id: 9, text: "Task #2", start_date:"11-04-2018", duration: 8, progress:0.6, parent:6 },
        { id: 10, text: "사람은 어떻게 기억하는가", start_date:"11-04-2018", duration: 8, progress:0.6, parent:1 },
        { id: 11, text: "Task #2", start_date:"11-04-2018", duration: 8, progress:0.6, parent:10 },
        { id: 12, text: "Task #2", start_date:"11-04-2018", duration: 8, progress:0.6, parent:10 },
        { id: 13, text: "Task #2", start_date:"11-04-2018", duration: 8, progress:0.6, parent:10 },
        { id: 14, text: "Task #2", start_date:"11-04-2018", duration: 8, progress:0.6, parent:10 },
        { id: 15, text: "사람은 어떻게 생각하는가", start_date:"11-04-2018", duration: 8, progress:0.6, parent:1 },
        { id: 16, text: "Task #2", start_date:"11-04-2018", duration: 8, progress:0.6, parent:15 },
        { id: 17, text: "Task #2", start_date:"11-04-2018", duration: 8, progress:0.6, parent:15 },
        { id: 18, text: "Task #2", start_date:"11-04-2018", duration: 8, progress:0.6, parent:15 },
        { id: 19, text: "Task #2", start_date:"11-04-2018", duration: 8, progress:0.6, parent:15 },
        { id: 20, text: "사람은 어떻게 주의를 집중하는가", start_date:"11-04-2018", duration: 8, progress:0.6, parent:1 },
        { id: 21, text: "Task #2", start_date:"11-04-2018", duration: 8, progress:0.6, parent:1 },
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
