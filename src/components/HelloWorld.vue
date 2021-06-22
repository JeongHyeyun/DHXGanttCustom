<template>
  <div>
    <div id="gantt_here" style='width:100%; height:100vh;'></div>
  </div>
</template>

<script>
/* eslint-disable */
import { gantt } from 'dhtmlx-gantt'
import 'dhtmlx-gantt/codebase/dhtmlxgantt.css';

import db from '../../firebaseInit';

import moment from 'moment'

// This import loads the firebase namespace along with all its type information.
// import firebase from 'firebase/app';

// These imports load individual services into the firebase namespace.
// import 'firebase/auth';
// import 'firebase/database';

export default {
  data () {
    return {
      ganttData: [],
    }
  },
  methods: {
    initGantt() {
      // 간트 plugin 설정
      gantt.plugins({ 
        marker: true 
      });
      // 마커 추가
      const markerId = gantt.addMarker({
        start_date: moment('2021-06-03'), //a Date object that sets the marker's date
        css: "today", //a CSS class applied to the marker
        text: "기준", //the marker title
      });
      gantt.getMarker(markerId);

      gantt.init('gantt_here')  // 간트 그리기
      gantt.parse({ data: this.ganttData });  // 간트 내 데이터 삽입
    }
  },
  created () {
    const ganttDatas = db.collection('ganttProjects');
    ganttDatas.get().then((response) => {
      for (const doc of response.docs) {
        const data = doc.data();
        data.id = doc.id;
        data.end_date = moment(data.endDate.toDate()).format('DD-MM-YYYY');
        data.start_date = moment(data.startDate.toDate()).format('DD-MM-YYYY');
        data.text = data.title;
        // 불필요한 데이터 삭제
        delete data.startDate;
        delete data.endDate;
        delete data.title;
        this.ganttData.push(data);
      }
    }).catch((error) => {
      console.log(error);
    }).finally(() => {
      this.initGantt();  // 간트 삽입
    });
  },
  mounted () {
  }
}
</script>

<style scoped>
</style>
