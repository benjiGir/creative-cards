<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-12">
        <nav-header @pageWasChanged="currentPage = $event"></nav-header>
        <keep-alive>
          <component :is="currentPage"></component>
        </keep-alive>
      </div>
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import CardFront from './components/card/CardFront.vue'
import CardBack from './components/card/CardBack.vue'
import CardInsideLeft from './components/card/CardInsideLeft.vue'
import CardInsideRight from './components/card/CardInsideRight.vue'

export default {
  data: function() {
    return {
      currentPage: 'cardFront'
    }
  },
  components: {
    navHeader: Header,
    cardFront: CardFront,
    cardBack: CardBack,
    cardInsideLeft: CardInsideLeft,
    cardInsideRight: CardInsideRight
  }
}
</script>

<style>
  body {
    font-family: Verdana, Geneva, sans-serif;
    color: #333
  }
  a {
    cursor: pointer;
  }
</style>
