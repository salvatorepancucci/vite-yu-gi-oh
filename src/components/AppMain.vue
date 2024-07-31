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
 
</template>

<style lang="scss" scoped>
@import './styles/generals.scss';

</style>
