<template>
  <div class="columns">
    <div class="rows column is-8">
      <div class="row" v-for="(row,index) in table" :key="index">
        <div class="fontsize columns" @click="isOpen = !isOpen" >
          <span class="column">{{ row.employer }}</span> 
          <span class="column">{{ row.jobTitle }}</span> 
          <span class="column">
            <span v-show="row.present=='TRUE'">Present, </span>
            <span>{{ row.duration }}</span>
          </span>
        </div>
        <div v-if="!isOpen">{{ row.jobInfo }}</div>
      </div> 
      <hr />
    </div>
  </div>
</template>

<script>
import Tabletop from 'tabletop'
import _ from 'lodash'
export default {
  data () {
    return {
      table: [],
      isOpen: false
    }
  },

  mounted () {
    Tabletop.init({  
      key: '1W-xMb9P4Xpnn4iOKgDsA7H1dzwED_Jm3gqewoIpzHGo',
      callback: this.showInfo,
      simpleSheet: true 
    })
  },

  methods: {
    showInfo(data,tabletop) {
      this.table = _.compact(tabletop.sheets('resume').elements)
    }
  }
}
</script>

<style lang="scss" scoped>
  @import "../assets/scss/variables.scss";

  .fontsize {
    font-size: $primary-f-size;
  }
</style>
