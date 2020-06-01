<template>
  <div class="hello">
    <h1>Year Progress</h1>
    <p>
      Today is {{CurrentDay}}
    </p>
    <p>
      We are {{Percentage}}% through the year
    </p>
    <p>
      We are {{daysDifference}} days through the year
    </p>
     <p>
      <button v-on:click="onRefresh">Refresh</button>
    </p>   
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    
  },
    data: function () {
    return {
      now : new Date()
    }
  },
  computed: {
    // a computed getter
    CurrentDay : function () {
      // `this` points to the vm instance
      var date = new Date()
      return date.getDate() + "/" +  (date.getMonth() + 1) + "/" +  date.getFullYear()
    },
    Percentage : function () {
      var nowDate = this.now /*new Date()*/
      var startOfYearDate = new Date()
      startOfYearDate.setDate(1)
      startOfYearDate.setMonth(0)
      startOfYearDate.setYear(nowDate.getFullYear())

      var msDifference = nowDate - startOfYearDate

      var endOfYearDate = new Date()
      endOfYearDate.setDate(1)
      endOfYearDate.setMonth(0)
      endOfYearDate.setYear(nowDate.getFullYear()+1)
      var msInYear = endOfYearDate - startOfYearDate

     return (msDifference/msInYear * 100).toFixed(2)
    },
    daysDifference : function () {
      var nowDate = this.now
      
      var startOfYearDate = new Date()
  
      startOfYearDate.setDate(1)
      startOfYearDate.setMonth(0)
      startOfYearDate.setYear(nowDate.getFullYear())
      startOfYearDate.setMilliseconds(0)
      startOfYearDate.setMinutes(0)
      startOfYearDate.setSeconds(0)
      startOfYearDate.setHours(0)

      var msDifference = (nowDate.getTime() - startOfYearDate.getTime())
      var daysDifference = Math.floor((msDifference) /(1000 * 60 * 60 * 24));
      return daysDifference

//      return nowDate.getTime()
  },
  },
  methods: {
    onRefresh : function () {
      this.now =  new Date()
    }
  },

  mounted() {
    this.now = new Date()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
