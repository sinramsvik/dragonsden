<template>
    <div class="level columns">
      <div class="level-left column" v-for="(row,index) in table" :key="index">
        <h1>{{ row.header }}</h1>
        <h2>{{ row.aboutHeader }}</h2>
      </div>
      <social class="level-right"></social>
    </div>
</template>

<script>
import Social from './Social.vue'
import Tabletop from 'tabletop'
import _ from 'lodash'
export default {
  components: { Social },
  data () {
    return {
      table: []
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
      this.table = _.compact(tabletop.sheets('header').elements)
    }
  }
}
</script>

<style lang="scss" scoped>
  .level-left h2 {
    color: #63707E;
  }
</style>

