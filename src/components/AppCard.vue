<script>
export default {
  name: 'AppCard',
  props: {
    card: Object
  }
}
</script>

<template>
 <div class="col-md-3 mb-3">
    <div class="card h-100">
      <img :src="card.card_images[0].image_url" class="card-img-top" :alt="card.name">
      <div class="card-body">
        <h5 class="card-title">{{ card.name }}</h5>
        <p class="card-text">{{ card.type }}</p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import './styles/generals.scss';

</style>
