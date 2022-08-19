<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? '(Favorited)' : '' }}</h2>
    <button @click="toggleFavorite()">Toggle Favorite</button>
    <button @click="showDetails()">{{ isShowDetails ? 'Hide' : 'Show' }} Details</button>
    <ul v-show="isShowDetails">
      <li><strong>Phone:</strong> {{ phoneNumber }}</li>
      <li><strong>Email:</strong> {{ emailAddress }}</li>
    </ul>
    <button @click="$emit('delete-contact', id)">Delete contact</button>
  </li>
</template>

<script>
export default {
  props: {
    id: {
      type: Number,
      required: true
    },
    name: {
      type: String,
      required: true
    },
    phoneNumber: {
      type: String,
      required: true
    },
    emailAddress: {
      type: String,
      required: true
    },
    isFavorite: {
      type: Boolean,
      required: false,
      default: false
    }
  },

  emits: ['toggle-favorite', 'delete-contact'],

  data() {
    return {
      isShowDetails: false
    };
  },

  methods: {
    showDetails() {
      this.isShowDetails = !this.isShowDetails;
    },

    toggleFavorite() {
      this.$emit('toggle-favorite', this.id);
    }
  }
}
</script>
