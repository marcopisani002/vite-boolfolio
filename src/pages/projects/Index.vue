<script>
import axios from "axios";

export default {
  name: "ProjectsIndexPage",
  data() {
    return {
      backendUrl: "http://localhost:8000",
      /**
       * @type {{cover_img: string, title: string, category_id: number, tags: array, id: number}[]}
       */
      projects: [],
    };
  },
  methods: {
    fetchProjects() {
      axios.get(this.backendUrl + "/api/projects").then((resp) => {
        this.projects = resp.data;
      });
    },
  },
  mounted() {
    this.fetchProjects();
  },
};
</script>

<template>
  <div class="container text-center">
    <h1 class="text-warning">Lista progetti</h1>
    <div style="margin-left:23rem" class="mt-5">

<div class="card mb-3 bg-warning " style="width: 20rem;" v-for="project in projects" :key="project.id">
  <img :src="project.cover_img" class="card-img-top img-fluid" />
  <div class="card-body">
    <h5 class="card-title mt-4">

      <router-link :to="{ name: 'projects.show', params: { id: project.id } }" class="text-decoration-none text-black "> <strong class="text-success  ">NOME:
        </strong><br>{{ project.name }} <br> <small class="text-primary"><u> (clicca per info)</u></small></router-link>
    </h5>
     <!-- <p class="card-text">
    <div v-for="tech in project.technologies" :key="tech.id"><strong class="text-primary">DESCRIZIONE:
        </strong>{{ tech?.name }}</div>
    </p>  -->
    <p class="card-text mt-4"><strong class="text-success ">DESCRIZIONE:
        </strong> <br>
        {{ project.description }} <br>
         </p>
  </div>
</div>
</div>

    
  </div>
</template>
