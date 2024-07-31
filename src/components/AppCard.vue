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

.card {
  border: none;
  background-color: #343a40;
  color: white;
  width: 70%;
  text-align: center;
}

.card-img-top {
  margin-bottom: 5px;
}

.card-body {
  padding: 10px;
}

.card-title {
  font-size: 0.875rem;
  font-weight: bold;
}

.card-text {
  font-size: 0.75rem;
  margin-bottom: 0.25rem;
}
</style>
