<template>
  <form @submit.prevent="newFriend">
    <div>
      <label for="name">Name:</label>
      <input id="name" type="text" v-model="enteredName" />
    </div>
    <div>
      <label for="phone">Phone:</label>
      <input id="phone" type="text" v-model="enteredPhone" />
    </div>
    <div>
      <label for="email">Email:</label>
      <input id="email" type="text" v-model="enteredEmail" />
    </div>
    <button>Add Contact</button>
  </form>
</template>

<script>
export default {
  emits: ['add-contact'],
  data() {
    return {
      enteredName: '',
      enteredEmail: '',
      enteredPhone: '',
      newContact: {},
    };
  },
  methods: {
    newFriend() {
      let number = Math.random();
      this.newContact = {
        name: this.enteredName,
        email: this.enteredEmail,
        phone: this.enteredPhone,
        id: new Date().toISOString(),
        isFavourite: number > 0.5 ? true : false,
      };
      console.log(this.newContact);
      this.$emit('add-contact', this.newContact);
      this.enteredName = '';
      this.enteredEmail = '';
      this.enteredPhone = '';
    },
  },
};
</script>
