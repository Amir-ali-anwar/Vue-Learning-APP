<template>
  <base-dailog v-if="isEmpty">
  <template #default>
    <p>Unfortunately, at least one input value is invalid.</p>
    <p>Please check all inputs and make sure you enter at least a few characters into each input field.</p>
  </template>
  <template #actions>
    <base-button @click="confirmError">Okay</base-button>
  </template>
</base-dailog>
  <base-card>
    <form @submit.prevent="submitdata">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" name="title" id="title" ref="titleInput" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          id="description"
          name="description"
          rows="3"
          ref="descInput"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input type="link" name="link" id="link" ref="linkInput" />
      </div>
      <div>
        <base-button :type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue';
import BaseCard from '../UI/BaseCard.vue';
export default {
  components: {
    BaseCard,
    BaseButton,
  },
  inject: ['addResources'],
  data() {
    return {
      isEmpty: false,
    };
  },
  methods: {
    submitdata() {
      const enteredTitle = this.$refs.titleInput.value;
      const enteredDescription = this.$refs.descInput.value;
      const enteredUrl = this.$refs.linkInput.value;
      if (
        enteredTitle.trim() === '' ||
        enteredDescription.trim() === '' ||
        enteredUrl.trim() === ''
      ) {
        this.isEmpty = true;
        return 
      }
      this.addResources(enteredTitle, enteredDescription, enteredUrl);
    },
  },
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
