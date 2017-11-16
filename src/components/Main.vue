<template>
  <div class = "main">
    <div class = "calendar">
      <select v-model="selected">
        <option v-for="option in options" v-bind:value="option.text">
          <h2>{{ option.text }}</h2>
          </option>
      </select>
      <ul>
        <li><button><h2>{{ date }}</h2></button></li>
      </ul>
    </div>
    <div class = "todo" v-for="todo in todos">
      <ul>
        <li>
          <radial-progress-bar :diameter="70"
            :completed-steps="completedSteps"
            :total-steps="totalSteps"
            >
            <stop offset="30%" :stop-color="startColor"/>
            <stop offset="100%" :stop-color="stopColor"/>
            {{ completedSteps }}%
          </radial-progress-bar>
        </li>
        <li><h3>{{todo.title}}</h3></li>
      </ul>
    </div>
    <img src="../assets/icon/Floating.png">
  </div>
</template>

<script>
  import RadialProgressBar from 'vue-radial-progress/dist/vue-radial-progress.min.js'

  export default {
  //   props: {
  //     startColor: {
  //       type: String,
  //       required: false,
  //       default: '#ef6327'
  //     },
  //     stopColor: {
  //       type: String,
  //       required: false,
  //       default: '#ef6327'
  //     }
  //   },
    computed: {
      date () {
        var today = new Date()
        var date = today.getDate()
        var dates = [ date - 3, date - 2, date - 1, date, date + 1, date + 2, date + 3 ]
        return dates
      }
      // month() {
      //   var monthNames = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
      //   var today = new Date();
      //   return monthNames[today.getMonth()];
      // }
    },
    name: 'Main',
    data () {
      return {
        completedSteps: 50,
        totalSteps: 100,
        todos: [
          { title: 'UI 디자인 완료하기' },
          { title: 'Mini project' },
          { title: '세미나 발표 준비하기' }
        ],
        selected: 'November',
        options: [
          { text: 'January' },
          { text: 'February' },
          { text: 'March' },
          { text: 'April' },
          { text: 'May' },
          { text: 'June' },
          { text: 'July' },
          { text: 'August' },
          { text: 'September' },
          { text: 'October' },
          { text: 'November' },
          { text: 'December' }
        ]
      }
    },
    components: {
      RadialProgressBar
    }
    // methods: {
    //   getDataFromServer: function() {
    //     this.date = this.getDataFromServer(dd);
    //   }
    // }
  }
</script>

<style scoped>
    .main {
        height: 45em;
        position: relative;
    }
    .calendar {
        background-color: rgb(64, 139, 179);
        height: 7.81em;
    }
    .todo {
        background-color: rgb(216, 231, 239);
        height: 4.87em;
        width: 20em;
        margin: auto;
        margin-top: 1.62em;
        padding-top: 0.5em;
    }
    h3 {
        margin-left:0.5em;
        text-align: center;
    }
    img {
        position: absolute;
        bottom: 2em;
        right: 2em;
    }
    ul {
      list-style:none;
      margin:0;
      padding:0;
    }
    li {
      margin: 0 0 0 0;
      padding: 0 0 0 0;
      border : 0;
      float: left;    
    }
    select {
      font-size: 1.6em;
      margin-top: 1.7em;
      color: #ffffff;
    }
</style>
