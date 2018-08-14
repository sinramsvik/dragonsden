<template>
  <div class="columns">
    <div class="column" v-for="(row,index) in table" :key="index">
      <img class="smile" src="../assets/icons/smile.svg">
      <p>{{ row.about }}</p>
    </div>
  </div>
</template>

<script>
import Tabletop from 'tabletop'
import _ from 'lodash'
export default {
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
      this.table = _.compact(tabletop.sheets('about').elements)
    }
  }
}
</script>

<style lang="scss">
  img.smile {
    width: 30px;
    & + p {
      color: #63707E;
    }
  }
</style>