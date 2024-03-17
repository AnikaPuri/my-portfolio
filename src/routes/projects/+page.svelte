<script>import projects from '$lib/projects.json';

import Project from "$lib/Project.svelte";

import Pie from "$lib/Pie.svelte";

</script>

<title>Project</title>
    <h1>{projects.length} Projects</h1>

    <Pie
    <svg viewBox="-50 -50 100 100">
      <circle cx="0" cy="0" r="50" fill="red" /> </svg> />
    <div class="projects">
      {#each projects as p}
        <article>
          <Project data={p} />
        </article>
      {/each}
    </div>