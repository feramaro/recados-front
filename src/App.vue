<template>
  <div id="app">
    <navbar />
    <div class="row p-3 m-3">
        <div class="card p-3" style="width: 18rem">
          <div class="card-body">
            <h5 class="card-title">Novo</h5>
            <h6 class="card-subtitle mb-2 text-muted">Criar Novo Recado</h6>
            <form id="createRecado" @submit="send($data)">
              <div class="form-group">
                <label for="autor">Autor</label>
                <input
                  v-model="autor"
                  type="text"
                  class="form-control"
                  id="autor" required
                />
              </div>
              <div class="form-group">
                <label for="exampleInputPassword1">Recado</label>
                <textarea
                  v-model="recado"
                  type="text"
                  class="form-control"
                  id="recado" required
                />
              </div>
              <button type="submit" class="btn btn-primary">Enviar</button>
            </form>
          </div>
        </div>
      <card
        v-for="item in recados"
        :key="item.id"
        :id="item.id"
        :autor="item.autor"
        :recado="item.recado"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Navbar from "./components/Navbar.vue";
import Card from "./components/Card.vue";
const serverip = "http://localhost:5000";
export default {
  name: "App",
  components: {
    Navbar,
    Card,
  },
  data() {
    return {
      autor: "",
      recado: "",
      recados: [],
    };
  },
  async mounted() {
   this.recados = await this.retreive();
  },
  methods: {
    retreive: async function() {
      let response = await axios.get(`${serverip}/recado`, {
        responseType: "json",
      });

      return response.data.recados;
    },
    send: async function(payload) {
      let recado = await axios.post(
        `${serverip}/recado`,
        {
          autor: payload.autor,
          recado: payload.recado,
        },
        {
          responseType: "json",
        }
      );
      alert(recado.data.status);
      this.recados = await this.retreive()
    },
  },
};
</script>

<style>
</style>
