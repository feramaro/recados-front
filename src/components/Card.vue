<template>
  <div class="card p-3 m-3" style="width: 18rem">
    <div class="card-body">
      <h5 class="card-title">{{ id }}</h5>
      <h6 class="card-subtitle mb-2 text-muted">{{ autor }}</h6>
      <p class="card-text">
        {{ recado }}
      </p>
      <button @click="remove()" type="button" class="btn btn-danger">
        Excluir
      </button>
    </div>
  </div>
</template>

<script>
import axios from "axios";
const serverip = `http://localhost:5000`
export default {
  name: "Card",
  props: {
    id: Number,
    autor: String,
    recado: String,
  },
  methods: {
    remove: async function () {
      let confirmRemove = confirm(`Deseja realmente deletar?`);
      if (confirmRemove) {
        let remove = await axios.delete(`${serverip}/recado/${this.id}`);
        alert(remove.data.status);
        location.reload()
      }
    },
  },
};
</script>

<style>
</style>