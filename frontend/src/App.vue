<template>
  <div id="app">
    <!-- <transition name="fade">
      <VHeadPiece v-if="showHeadPiece"/>
    </transition> -->
      <vHeader />
      <section class="content">
          <keep-alive>
              <router-view></router-view>
          </keep-alive>
      </section>
      <vFooter/>
  </div>
</template>

<script>

import vHeader from './components/vHeader';
import vFooter from './components/vFooter';
import VHeadPiece from './components/vHeadpiece'
  export default {
    name: 'App',
    components: {
      vHeader,
      vFooter,
      VHeadPiece
    },
    data(){
      return{
        showHeadPiece: true
      }
    },
    mounted(){
      setTimeout(()=>this.showHeadPiece=false, 2000)
    }
  }
</script>


<style lang="scss">
    .content {
        min-height: calc(100vh - 464px);
        padding: 0 40px;
    }
</style>

