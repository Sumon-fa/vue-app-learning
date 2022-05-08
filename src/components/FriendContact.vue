<template>
  <ul>
    <li>
      <h2>{{ name }} {{ isFavourite ? 'Favourite' : '' }}</h2>
      <button @click="toogleFavourite">toogle-favourite</button>
      <button @click="toogleDetails">
        {{ detailsAreVisible ? 'Hide' : 'Show' }} Details
      </button>
      <ul v-if="detailsAreVisible">
        <li><strong>Phone:</strong> {{ phoneNumber }}</li>
        <li><strong>Email:</strong> {{ email }}</li>
      </ul>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    id: { type: String, required: true },
    name: { type: String, required: true },
    phoneNumber: { type: String, required: true },
    email: { type: String, required: true },
    isFavourite: { type: Boolean, required: false },
  },
  emits: {
    'toogle-favourite': function (id) {
      if (id) {
        return true;
      } else {
        console.warn('Missing id parameter!');
        return false;
      }
    },
  },

  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toogleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toogleFavourite() {
      this.$emit('toogle-favourite', this.id);
    },
  },
};
</script>
