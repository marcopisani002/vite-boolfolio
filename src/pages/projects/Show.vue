<script>
import axios from "axios";
export default {
  name: "ProjectsShow",
  data() {
    return {
      backendUrl: "http://localhost:8001",
      project: {},
    };
  },
  mounted() {
    axios
      .get(this.backendUrl + "/api/projects/" + this.$route.params.id)
      // .get(`${ this.backendUrl }/api/projects/${ this.$route.params.id }`)
      .then((resp) => {
        this.project = resp.data;
      })
      .catch((er) => {
        // in caso di errore non ha senso che l'utente rimanga qui
        // faccio un redirect su projects.index
        this.$router.push({ name: "projects.index" });
      });
  },
};
</script>

<template>
  <div class="container">
    <h1>Pagina dettagli post {{ $route.params.id }}</h1>
    <h2>{{ post.name }}</h2>

    <div >
      <img :src="post.cover_img" class="img-fluid" />
    </div>

    <p class="lead">{{ post.description }}</p>
  </div>
</template>
