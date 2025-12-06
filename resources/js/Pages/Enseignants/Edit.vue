<template>
  <div>
    <h1>Modifier Enseignant</h1>
    <form @submit.prevent="submit">
      <div>
        <label>Matricule</label>
        <input v-model="form.matricule" required>
      </div>
      <div>
        <label>Nom</label>
        <input v-model="form.nom" required>
      </div>
      <div>
        <label>Prénom</label>
        <input v-model="form.prenom" required>
      </div>
      <div>
        <label>Spécialité</label>
        <input v-model="form.specialite" required>
      </div>
      <button type="submit">Mettre à jour</button>
    </form>
  </div>
</template>

<script>
import { Inertia } from '@inertiajs/inertia'

export default {
  props: {
    enseignant: Object
  },
  data() {
    return {
      form: {...this.enseignant}
    }
  },
  methods: {
    submit() {
      Inertia.put(`/enseignants/${this.form.id}`, this.form)
    }
  }
}
</script>
