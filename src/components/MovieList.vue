<template>
    <div id="movie-list">
        <div v-for="movie in filteredMovies" class="movie">{{ movie.title }}</div>
    </div>
</template>
<script>
    import genres from '../util/genres';

    export default {
        props: ['genre', 'time'],
        data() {
            return {
                movies: [
                    { title: 'Pulp Fiction', genre: genres.CRIME },
                    { title: 'Home Alone', genre: genres.COMEDY },
                    { title: 'Rogue One', genre: genres.COMEDY }
                ]
            };

        },
        methods: {
            moviePassesGenreFilter(movie) {
                if (!this.genre.length) {
                    return true;
                }
                return this.genre.find(genre => movie.genre === genre);
            }
        },
        computed: {
            filteredMovies() {
                return this.movies.filter(this.moviePassesGenreFilter);
            }
        }
    }
</script>