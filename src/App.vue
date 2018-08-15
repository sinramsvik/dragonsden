<template>
  <div id="app" class="margins">
    <desktop-header class="spacer"></desktop-header>
    <client-list class="spacer"></client-list>
    <about class="spacer"></about>
    <resume></resume>
  </div>
</template>

<script>
import DesktopHeader from './components/DesktopHeader.vue'
import ClientList from './components/ClientList.vue'
import About from './components/About.vue'
import Resume from './components/Resume.vue'
export default {
  name: 'app',
  components: {
    About, 
    DesktopHeader,
    ClientList,
    Resume
  },
  data () {
    return {

    }
  }
}
</script>

<style lang="scss">
  @import '/assets/scss/app';
  .margins {
    margin: 55px 80px;
  }
</style>
