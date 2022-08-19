<template>
  <form @submit.prevent="addContact()">
    <div>
      <label for="name">Name: </label>
      <input type="text" id="name" name="name" v-model="name" />
    </div>

    <div>
      <label for="phone">Phone: </label>
      <input type="tel" id="phone" name="phone" v-model="phone" />
    </div>

    <div>
      <label for="email">Email: </label>
      <input type="email" id="email" name="email" v-model="email" />
    </div>

    <div>
      <button>Add contact</button>
    </div>
  </form>
</template>

<script>
export default {
  emits: ['add-contact'],

  data() {
    return {
      name: '',
      phone: '',
      email: ''
    };
  },

  methods: {
    addContact() {
      const newContact = {
        id: new Date().toISOString(),
        name: this.name,
        phoneNumber: this.phone,
        emailAddress: this.email,
        isFavorite: false
      };

      this.$emit('add-contact', newContact);
      this.name = '';
      this.phone = '';
      this.email = '';
    }
  }
}
</script>
