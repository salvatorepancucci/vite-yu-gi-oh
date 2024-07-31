<script>
import axios from 'axios'
import AppCard from './AppCard.vue'

export default {
  name: 'AppMain',
  components: {
    AppCard
  },
  data() {
    return {
      cards: []
    }
  },
  created() {
    axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
      .then(response => {
        this.cards = response.data.data
      })
  }
}
</script>

<template>
 <main>
    <div class="container">
      <div class="row">
        <AppCard
          v-for="card in cards"
          :key="card.id"
          :card="card"
        />
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>
@import './styles/generals.scss';

main {
    background-color: $primary-color;
}
</style>
