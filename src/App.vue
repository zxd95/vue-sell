<template>
  <div id="app">
    <v-header :seller="seller"></v-header>
    <header-detail></header-detail>
    <div class="tab-wrapper">
      <tab :tabs="tabs"></tab>
    </div>
  </div>
</template>

<script>
import VHeader from 'components/v-header/v-header'
import HeaderDetail from 'components/header-detail/header-detail'
import Tab from 'components/tab/tab'
import { getSeller } from 'api'

export default {
  name: 'app',
  components: {
    VHeader,
    HeaderDetail,
    Tab
  },
  data () {
    return {
      seller: {}
    }
  },
  computed: {
    tabs () {
      return []
    }
  },
  created () {
    this._getSeller()
  },
  methods: {
    _getSeller () {
      getSeller().then((seller) => {
        this.seller = seller
      })
    }
  }
}
</script>

<style lang="stylus" scoped>
#app {
  .tab-wrapper {
    position: fixed;
    top: 136px;
    left: 0;
    right: 0;
    bottom: 0;
  }
}
</style>
