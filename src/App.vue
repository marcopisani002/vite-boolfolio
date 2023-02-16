<script>
import TheHeader from "./TheHeader.vue";
import axios from "axios";

export default {
  components: { TheHeader },
  data() {
    return {
      backendUrl: "http://localhost:8000",
      /**
       * @type {{cover_img: string, title: string, category_id: number, tags: array, id: number}[]}
       */
      posts: [],
    };
  },
  methods: {
    fetchPosts() {
      axios.get(this.backendUrl + "/api/projects").then((resp) => {
        this.posts = resp.data;

      });
    },
  },
  mounted() {
    this.fetchPosts();
  },
};

</script>

<template>
  <TheHeader></TheHeader>
  <!-- In Blade usavamo lo @yield("content") -->
  <!-- In vue-router usiamo il tag router-view -->
  <!-- <router-view></router-view> -->
  <div class="container text-center">
    <h1 class="text-primary">Lista progetti</h1>





    <div style="margin-left:11rem" class="mt-5">

      <div class="card mb-3 bg-warning" style="width: 20rem;" v-for="post in posts" :key="post.id">
        <img :src="post.cover_img" class="card-img-top img-fluid" />
        <div class="card-body">
          <h5 class="card-title">

            <router-link :to="{ name: 'posts.show', params: { id: post.id } }"> <strong class="text-primary">NOME:
              </strong>{{ post.name }}</router-link>
          </h5>
          <p class="card-text">
          <div v-for="tech in post.technologies" :key="tech.id"><strong class="text-primary">TECNOLOGIA:
              </strong>{{ tech.name }}</div>
          </p>
    
        </div>
      </div>
    </div>







   
</div>
</template>

<style lang="scss">
@use "main.scss";

body {
  min-height: 100vh;

  background: linear-gradient(12deg, rgb(20, 193, 223) 0%, rgba(10, 155, 10, 0.786) 50%, rgb(25, 224, 148) 100%);
}</style>
