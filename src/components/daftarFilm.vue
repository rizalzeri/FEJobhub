<template>
  <div>
    <nav>
      <ul class="justify-content-center">
        <li><h2>Daftar Film</h2></li>
      </ul>
    </nav>

    <ul class="film-list">
      <li v-for="show in shows" :key="show.show.id">
        <div class="film-image">
          <img :src="show.show.image.medium" :alt="show.show.name" />
        </div>
        <h2>{{ show.show.name }}</h2>
      </li>
    </ul>
    <div>
      <footer
        class="text-center text-lg-start"
        style="background-color: #333"
      >
        

        <!-- Copyright -->
        <div
          class="text-center text-white p-3"
          style="background-color: rgba(0, 0, 0, 0.2)"
        >
          © 2023 Copyright:
          <a class="text-white" href="https://jobhun.id/"
            >JobHun</a
          >
        </div>
        <!-- Copyright -->
      </footer>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      shows: [],
    };
  },
  mounted() {
    axios
      .get("http://api.tvmaze.com/search/shows?q=girls")
      .then((response) => {
        this.shows = response.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style>
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
  background-color: #333;
  color: #fff;
}
nav ul {
  display: flex;
  list-style: none;
}
nav ul li {
  margin-right: 1rem;
}

nav img {
  height: 50px;
  width: 100px;
}
.film-list {
  display: flex;
  flex-wrap: wrap;
  list-style: none;
  margin: 0;
  padding: 0;
}
.film-list li {
  flex-basis: calc(50% - 1rem);
  margin-right: 1rem;
  margin-bottom: 1rem;
  padding: 1rem;
  background-color: #eee;
  border-radius: 0.5rem;
  box-shadow: 0 2px 2px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.film-list li:last-child {
  margin-right: 0;
}
.film-image {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 200px;
}
.film-image img {
  max-height: 100%;
  max-width: 100%;
}
.film-list li h2 {
  margin-top: 1rem;
  margin-bottom: 0;
  font-size: 1.2rem;
}
</style>