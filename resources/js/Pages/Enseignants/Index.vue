<template>
  <div>
    <h1>Liste des Enseignants</h1>
    <inertia-link href="/enseignants/create">Ajouter un enseignant</inertia-link>

    <table border="1" cellpadding="5">
      <thead>
        <tr>
          <th>Matricule</th>
          <th>Nom</th>
          <th>Prénom</th>
          <th>Spécialité</th>
          <th>Étudiants</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="enseignant in enseignants" :key="enseignant.id">
          <td>{{ enseignant.matricule }}</td>
          <td>{{ enseignant.nom }}</td>
          <td>{{ enseignant.prenom }}</td>
          <td>{{ enseignant.specialite }}</td>
          <td>
            <ul>
              <li v-for="etudiant in enseignant.etudiants" :key="etudiant.id">
                {{ etudiant.nom }} {{ etudiant.prenom }}
              </li>
            </ul>
          </td>
          <td>
            <inertia-link :href="`/enseignants/${enseignant.id}/edit`">Modifier</inertia-link>
            <form :action="`/enseignants/${enseignant.id}`" method="POST" style="display:inline">
              <input type="hidden" name="_method" value="DELETE">
              <input type="hidden" name="_token" :value="csrf">
              <button type="submit">Supprimer</button>
            </form>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    enseignants: Array,
    csrf: String,
  },
}
</script>
