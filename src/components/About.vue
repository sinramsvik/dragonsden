<template>
  <section class="columns">
    <div class="column rows" v-for="(row,index) in table" :key="index">
      <img class="smile row" src="../assets/icons/smile.svg">
      <svg height="2" width="55" class="row">
        <line x1="55" y1="0" x2="0" y2="0" />
      </svg>
      <p class="row">{{ row.about }}</p>
      <p class="row">{{ row.aboutTwo }}</p>
    </div>
  </section>
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
@import "../assets/scss/variables.scss";

  img.smile {
    width: 30px;
    display: block;
    & + svg {
      stroke: $secondary;
      stroke-width: 2px;
    }
    & ~ p {
    color: $subtext-gray;
    padding-bottom: 16px;
    }
  }

</style>