<template>
	<!-- My Projects -->
	<section class="pb-5" id="projects">
	        <h1 class="mt-5 mb-5 pb-4 text-center">My Projects</h1>
	    <!-- 1st Projects Placeholder-->
	    <!-- we will use the v-for directive to loop through the large array -->
	    <div class="card-deck my-5 justify-content-center" v-for="(group, index) in chunckedProjects" :key="index">
	    	<!-- In the smaller arrays of 3, we will loo through the individual projects to ccreate a project card for each -->
	    	<ProjectCard v-for="project in group" :key="project.id" :project="project" />
	    </div>
	    <!-- End of 3rd Projects Placeholder-->

	</section>
</template>

<script setup>
	// import the 'computed' method to define reactive derived state
	import { computed } from 'vue';
	//  import the projectcard which will display the individual rpoject details
	import ProjectCard from './ProjectCard.vue';
	// import projects.json to retrieve the project details
	import projects from '../data/projects.json';

	// define the number of projects to be displayed per row
	const chunkSize = 3;

	// the main purpose of the function is to create smaller arrays inside of the projects that contains 3 projects each
	/*
	chunckedProjects = [
		[
			project1,
			project2,
			project3
		],
		[
			project1,
			project2,
			project3
		],
		[
			project1,
			project2,
			project3
		]
	]
	*/
	const chunckedProjects = computed(() => {
		const chunks = [];

		for (let i = 0; i < projects.length; i+= chunkSize) {
			chunks.push(projects.slice(i, i + chunkSize));
		}

		return chunks;
	})
	
</script>