<template>
  <div class="q-pa-md" style="max-width: 400px">

    
    <q-form class="q-gutter-md">
      <q-input filled v-model="name" label="Your name *" lazy-rules
        :rules="[val => val.length < 15 || 'Name Invalid']" />

      <q-input filled type="number" v-model="age" label="Your age *" lazy-rules :rules="[
      val => val !== null && val !== '' || 'Please type your age',
      val => val > 0 && val < 100 || 'Please enter an age between 1 - 100'
    ]" />

      <div>
        <q-btn @click="generateRandomPerson" label="Generate Random Person" type="submit" color="primary" />
        <q-btn @click="onReset" label="Reset" color="primary" flat class="q-ml-sm" />
      </div>
    </q-form>

    <q-card class="my-card bg-secondary text-white q-mt-md">
      <q-card-section>
        <div class="text-h6">Details:</div>
        <div class="text-subtitle2">My Name Is {{ name }} And I'm {{ age }} yeard old</div>
        <div class="text-subtitle3">In 10 years I will be {{ agePlusTen }}</div>
        <div class="text-subtitle4">My name is {{ name.length }} characters long</div>
        <div class="text-subtitle5">My name in uppercase is {{ uppercase }}</div>
      </q-card-section>

    </q-card>


  </div>
</template>

<script>
import { useQuasar } from 'quasar'
import { ref } from 'vue'

export default {
  data() {
    return {
      name: 'Jenny',
      age: 13,
      names: ['Kahfi', 'John', 'Rick', 'Lisa']
    }
  },
  computed: {
    agePlusTen() {
      return parseInt(this.age) + 10
    },
    uppercase() {
      return this.name.toUpperCase()
    },
  },
  methods: {
    onReset() {
      this.name = null
      this.age = null
    },
    generateRandomPerson(){
      this.name = this.names[Math.floor(Math.random() * this.names.length)]
      this.age = Math.floor(Math.random() * 99) + 1
    }
  }
}
</script>

<style></style>

