<script>import projects from '$lib/projects.json';

import Project from "$lib/Project.svelte";

</script>

<title>Project</title>
    <h1>{projects.length} Projects</h1>

    <div class="projects">
      {#each projects as p}
        <article>
          <Project data={p} />
        </article>
      {/each}
    </div>