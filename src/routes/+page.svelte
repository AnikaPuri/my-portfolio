<script>import projects from '$lib/projects.json';

    import Project from "$lib/Project.svelte";
    
    </script>


<title>Anika Puri: Personal Site and Portfolio</title>
<h1>Anika Puri</h1>
<p>Hi! My name is Anika Puri and I'm currently a sophomore at MIT majoring in 6-4.</p>
<img src="images/AnikaPuri_Photo (2).jpg" alt="picture of Anika Puri in the woods jpg" width="300" height=auto />

<h2>Latest Projects</h2>
    <div class="projects">
      {#each projects.slice(0, 3) as p}
        <article>
            <Project data={p} hLevel=3 />
        </article>
      {/each}
    </div>