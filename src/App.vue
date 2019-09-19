<template>
<div class="container">
	<div class="navbar"></div>
	<div class="content"></div>
	<div class="footer"></div>
	<h3>{{ posts.title }}</h3>
	<p>{{ posts.description }}</p>
	<p>{{ postes.name }}</p>
	<p>{{ postese.name }}</p>
</div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
	return {
		posts: [],
		postes: [],
		postese: []
	}
  },
  mounted() {
	axios.all([
		axios.get('https://ghibliapi.herokuapp.com/films/58611129-2dbc-4a81-a72f-77ddfc1b1b49'),
		axios.get('https://ghibliapi.herokuapp.com/people/986faac6-67e3-4fb8-a9ee-bad077c2e7fe'),
		axios.get('https://ghibliapi.herokuapp.com/people/d5df3c04-f355-4038-833c-83bd3502b6b9'),
	  ])
	  .then(axios.spread((filmRes, peopleRes, peopleRes2) => {
		this.posts = filmRes.data;
		this.postes = peopleRes.data;
		this.postese = peopleRes2.data;
		console.log('Data 1: ', filmRes.data);
		console.log('Data 2: ', peopleRes.data);
		console.log('Data 3: ', peopleRes2.data);
	  }))
	  .catch( function(error){
		console.log('Error: ', error);
	  })
  
  
	
  }
}
</script>

<style>
	.title{
		width: 500px;
		height: 50px;
		display: grid;
		  }
</style>
