<template>
	<div class="app">
		<header>
			<h1>The<strong>Anime</strong>Database</h1>

			<form class="search-box" @submit.prevent="HandleSearch">
				<input 
					type="search" 
					class="search-field" 
					placeholder="Search for an anime..."
					required
					v-model="search_query" />
			</form>
		</header>
		<main>
			<div class="cards" v-if="animelist.length > 0">
				<Card 
					v-for="anime in animelist" 
					:key="anime.mal_id"
					:anime="anime" />
			</div>
			<div class="no-results" v-else>
				<h3>Sorry, we have no results...</h3>
			</div>
		</main>
	</div>
</template>

<script>
import { ref } from 'vue';
import Card from './components/Card';
export default {
	setup() {
		const search_query = ref("");
		const animelist = ref([]);
		const HandleSearch = async () => {
			animelist.value = await fetch(`https://api.jikan.moe/v3/search/anime?q=${search_query.value}`)
				.then(res => res.json())
				.then(data => data.results);
			search_query.value = "";
		}
		return {
			Card,
			search_query,
			animelist,
			HandleSearch
		}
	}
}
</script>

<style >
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  font-weight: bold;
}
a {
  text-decoration: none;
}
header {
  padding-top: 50px;
  padding-bottom: 50px;

}


  h1{
    color: #888;
    text-align: center;
    font-size: 42px;
    font-weight: 400;
    text-transform: uppercase;
    margin-bottom: 30px;


  }
  h1:hover{
    color: #313131;
  }
    strong {
      color: #313131;
    }

  .search-box {
    display: flex;
    justify-content: center;
    padding-left: 30px;
    padding-right: 30px;

  }
  .search-field {
      appearance: none;
      background: none;
      border: none;
      outline: none;
      background-color: #f3f3f3;
      box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.15);
      display: block;
      width: 100%;
      max-width: 600px;
      padding: 15px;
      border-radius: 8px;

      color: #313131;
      font-size: 20px;

    }

  main {
    max-width: 1200px;
    margin: 0 auto;
    padding-left: 30px;
    padding-right: 30px;
    }
    .cards {
      display: flex;
      flex-wrap: wrap;
      margin: 0 -8px;
    }
    
</style>
