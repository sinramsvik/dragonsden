<template>
  <section class="rows">
    <div class="row" @click="isOpen = !isOpen" v-for="(row,index) in table" :key="index">
      <div class="columns">
        <span class="column is-4">{{ row.employer }}</span>
        <span class="column is-4">{{ row.jobTitle }}</span>
        <span class="column right"><span v-show="row.present=='TRUE'">Present, </span>{{ row.duration }}</span>
        <span class="column right"><img src="../assets/icons/arrow.svg" :class="{'arrowup': isOpen}"></span>
      </div>
      <div class="jobinfo" v-if="isOpen">{{ row.jobInfo }}</div>
      <hr />
    </div>
  </section>
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

  .jobinfo {
    color: $subtext-gray;
    margin-bottom: 12px;
  }
  hr {
    margin: 0;
  }
  .columns:not(:last-child) {
    margin-bottom: 0; 
  }
  .column {
    margin-top: 12px;
  }
  .right {
    text-align: right;
  }
  .arrowup {
    transform: rotate(180deg);
  }

</style>
