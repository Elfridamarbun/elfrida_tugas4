<template>
    <div class="film-list">
      <h2>Daftar Film Dibioskop</h2>
      <ul>
        <FilmItem 
          v-for="film in films" 
          :key="film.id" 
          :film="film" 
          :is-selected="film.id === selectedFilmId"
          @select-film="selectFilm"
        />
      </ul>
      <slot name="detail"></slot>
    </div>
  </template>
  
  <script>
  import FilmItem from './FilmItem.vue';
  
  export default {
    components: { FilmItem },
    data() {
      return {
        films: [
          { id: 1, title: 'Fast And Forious', director: 'Justin Lin', genre: 'Action' },
          { id: 2, title: 'The Dark Knight (2008)', director: 'Christopher Nolan', genre: 'Action' },
          { id: 3, title: 'The Lion King (1994)', director: 'Roger Allers, Rob Minkoff', genre: 'Animation' }
        ],
        selectedFilmId: null
      };
    },
    methods: {
      selectFilm(film) {
        this.selectedFilmId = film.id;
        this.$emit('film-selected', film);
      }
    }
  };
  </script>
  
  <style scoped>
  .film-list {
    padding: 20px;
    background-color: #f3f6f6;
    border: 1px solid #ddd;
    border-radius: 8px;
  }
  .film-list h2 {
    color: #7997d7;
  }
  .film-list ul {
    list-style-type: none;
    padding: 0;
  }
  </style>
  