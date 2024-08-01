<template>
  <main>
    <div class="container">
      <div class="row mb-3 justify-content-center">
        <div class="col-auto">
          <select class="btn btn-primary" v-model="selectedArchetype" @change="fetchCardsByArchetype">
            <option value="">Select Archetype</option>
            <option v-for="archetype in limitedArchetypes" :key="archetype" :value="archetype">{{ archetype }}</option>
          </select>
        </div>
      </div>
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
      cards: [],
      archetypes: [],
      selectedArchetype: ''
    }
  },
  computed: {
    limitedArchetypes() {
      return this.archetypes.slice(0, 20);
    }
  },
  created() {
    this.fetchArchetypes();
    this.fetchCards();
  },
  methods: {
    fetchArchetypes() {
      axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php')
        .then(response => {
          this.archetypes = response.data.map(item => item.archetype_name);
        })
        .catch(error => {
          console.error('Error loading archetypes', error);
        });
    },
    fetchCards() {
      axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
        .then(response => {
          this.cards = response.data.data;
        })
        .catch(error => {
          console.error('Error loading cards', error);
        });
    },
    fetchCardsByArchetype() {
      if (this.selectedArchetype) {
        axios.get(`https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=${this.selectedArchetype}`)
          .then(response => {
            this.cards = response.data.data;
          })
          .catch(error => {
            console.error('Error loading cards by archetype', error);
          });
      } else {
        this.fetchCards();
      }
    }
  }
}
</script>

<style lang="scss" scoped>
@import './styles/generals.scss';

main {
    background-color: $primary-color;
}

select.btn {
  padding: 0.5rem 1rem;
  font-size: 1rem;
  cursor: pointer;
  border: none;
  color: white;
  background-color: $primary-color;
  border-radius: 5px;
}

select.btn:hover {
  background-color: darken($primary-color, 10%);
}
</style>