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

    {#await fetch("https://api.github.com/users/AnikaPuri") }
    <p>Loading...</p>
  {:then response}
    {#await response.json()}
      <p>Decoding...</p>
    {:then data}
      <section>
        <h2>My GitHub Stats</h2>     
        <dl>
          <dt>Followers</dt>
          <dd>{data.followers}</dd>
        
          <dt>Following</dt>
          <dd>{data.following}</dd>
        
          <dt>Login</dt>
          <dd>{data.login}</dd>
        </dl> 
      </section>
    {:catch error}
      <p class="error">
        Something went wrong: {error.message}
      </p>
    {/await}
  {:catch error}
    <p class="error">
      Something went wrong: {error.message}
    </p>
  {/await}