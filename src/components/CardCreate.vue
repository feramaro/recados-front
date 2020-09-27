<template>
  <div class="card p-3" style="width: 18rem">
    <div class="card-body">
      <h5 class="card-title">Novo</h5>
      <h6 class="card-subtitle mb-2 text-muted">Criar Novo Recado</h6>
      <form id="createRecado" @submit="create">
        <div class="form-group">
          <label for="autor">Autor</label>
          <input v-model="autor" type="text" class="form-control" id="autor" />
        </div>
        <div class="form-group">
          <label for="exampleInputPassword1">Recado</label>
          <textarea
            v-model="recado"
            type="text"
            class="form-control"
            id="recado"
          />
        </div>
        <button type="submit" class="btn btn-primary">Enviar</button>
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "CardCreate",
  data() {
    return {
      autor: "",
      recado: "",
    };
  },
};
</script>

<style>
</style>