<template>
  <div class="home">
  <h1>Adopt a new best friend.</h1>
  <button @click="togglePetForm" class="btn btn-primary">Add New Pet</button>

  <b-form @submit.prevent="handleSubmit" v-if="showPetForm">

      <b-form-group id="input-group-2" label="Pets Name:" label-for="input-2">
        <b-form-input
          id="input-2"
          type="text"
          v-model="form.name"
          required
          placeholder="Enter name"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Species:" label-for="input-3">
        <b-form-select
          id="input-3"
          v-model="form.food"
          :options="['cats','dogs']"
          required
        ></b-form-select>
      </b-form-group>

      <b-form-group id="input-group-2" label="Pets Age:" label-for="input-2">
        <b-form-input
          id="input-2"
          type="number"
          v-model="formData.age"
          required
          placeholder="Enter age"
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
</b-form>

  </div>
</template>

<script>

import { mapActions } from 'vuex'
export default {
  name: 'home',
  data() {
    return {
      showPetForm: false,
      formData: {
        name: '',
        age: 0,
        species: null
      }
    }
  },
  methods: {
    ...mapActions([
      'addPet'
    ]),
    togglePetForm() {
      this.showPetForm = !this.showPetForm
    },

    handleSubmit() {
      const payload = {
          const { species, age, name } = !this.formData
          const payload = {
          pet : {
            name,
            age
          }
        }
      this.addPet(payload)

      this.formData = {
        name: '',
        age: 0,
        species: null

      }
      }
    }
  }
}
</script>
