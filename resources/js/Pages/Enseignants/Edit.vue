<template>
  <div>
    <h1>Modifier un enseignant</h1>
    <form @submit.prevent="submit">
      <input v-model="matricule" placeholder="Matricule" required />
      <input v-model="nom" placeholder="Nom" required />
      <input v-model="prenom" placeholder="Prénom" required />
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
      matricule: this.enseignant.matricule,
      nom: this.enseignant.nom,
      prenom: this.enseignant.prenom
    }
  },
  methods: {
    submit() {
      Inertia.put(`/enseignants/${this.enseignant.id}`, {
        matricule: this.matricule,
        nom: this.nom,
        prenom: this.prenom
      })
    }
  }
}
</script>
