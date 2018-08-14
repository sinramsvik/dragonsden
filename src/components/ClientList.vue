<template>
  <div>
    <hr />
    <div class="columns is-multiline">
      <div class="column is-2-desktop is-3 is-4" v-for="(row,index) in table" :key="index">
        <popper trigger="hover" :options="{placement: 'auto'}">
          <div class="popper">
            <img :src="row['photo-url']">
            <p>{{ row.clientBody }}</p>
          </div>
          <p class="client" slot="reference">{{ row.client }}</p>
        </popper>
      </div>
    </div>
    <hr />
  </div>
</template>

<script>
import Tabletop from 'tabletop'
import Popper from 'vue-popperjs'
import _ from 'lodash'
export default {
  components: {
      Popper
  },
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
      this.table = _.compact(tabletop.sheets('work').elements)
    }
  }
}
</script>

<style lang="scss" scoped>
  @import "../assets/scss/variables.scss";

  .client {
    line-height: 30px;
    padding-left: 8px;
    &:hover {
      background-color: #eaeaea;
      border-radius: 4px;
    }
  }
  .popper p {
    font-size: $primary-f-size;
  }
  // Variations
  .popper {
    width: 320px;
    height: 320px;
    background-color: #fff;
    box-shadow: 0px 3px 36px 0px rgba(0,0,0,0.2);
    padding: 1rem;
  }
  .column {
    padding: 0;
  }
</style>