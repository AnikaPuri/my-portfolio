<script>import projects from '$lib/projects.json';

import Project from "$lib/Project.svelte";

import * as d3 from 'd3';

import Pie from "$lib/Pie.svelte";


// let data = [
// 	{ value: 1, label: "apples" },
// 	{ value: 2, label: "oranges" },
// 	{ value: 3, label: "mangos" },
// 	{ value: 4, label: "pears" },
// 	{ value: 5, label: "limes" },
// 	{ value: 5, label: "cherries" }
// ];

let filteredProjects;
$: filteredProjects = projects.filter(project => {
	let values = Object.values(project).join("\n").toLowerCase();
	return values.includes(query.toLowerCase());
});

let rolledData;

// Make sure the variable definition is *outside* the block
let pieData;

$: {
	// Initialize to an empty object every time this runs
	pieData = {};
  rolledData = d3.rollups(filteredProjects, v => v.length, d => d.year);

  pieData = rolledData.map(([year, count]) => {
	return { value: count, label: year };
});

	// Calculate rolledData and pieData based on filteredProjects here
}
let query = "";



let selectedYearIndex = -1;

let selectedYear;
$: selectedYear = selectedYearIndex > -1 ? pieData[selectedYearIndex].label : null;


let filteredProjectsYear;
$: filteredProjectsYear = filteredProjects.filter(project => {
  if (selectedYearIndex !== -1)
   return project.year === selectedYear;
  else
    return true;
})



</script>

<title>Project</title>
    <h1>{projects.length} Projects</h1>

  <Pie data={pieData} bind:selectedIndex={selectedYearIndex} />


  <input type="search" bind:value={query}
  aria-label="Search projects" placeholder="🔍 Search projects…" />



    <div class="projects">
      {#each filteredProjectsYear as p}
        <article>
          <Project data={p} />
        </article>
      {/each}
    </div>

  <style>

  </style>