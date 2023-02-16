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

      .then((resp) => {
        this.project = resp.data;
      })
   
  },
};
</script>

<template>
  <div class="container text-center text-warning mt-4">
    <h1>Pagina dettagli progetto {{ $route.params.id }}</h1>
    <h2>{{ project.name }}</h2>

    <div >
      <img :src="project.cover_img" class="img-fluid" />
    </div>

    <p class="lead">{{ project.description }}</p>
  </div>
</template>
