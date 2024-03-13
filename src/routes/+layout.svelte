


<script> 
// this is where all the java script goes

let pages = [
	{url: "./", title: "Home"},
	{url: "./projects", title: "Projects"},
    {url: "./resume", title: "Resume"},
    {url: "./contact", title: "Contact"},
    {url: "https://github.com/AnikaPuri", title: "Profile"}]

let root = globalThis?.document?.documentElement;

let localStorage = globalThis.localStorage ?? {};

let colorScheme = localStorage.colorScheme ?? "light dark";

$: localStorage.colorScheme = colorScheme;

root?.style.setProperty("color-scheme", colorScheme);

$: root?.style.setProperty("color-scheme", colorScheme);

let profileData = fetch("https://api.github.com/users/AnikaPuri");

</script>

<!-- if not in a script / style then it's html -->




<nav>
    {#each pages as p}
      <a href="{p.url}">{p.title}</a>
    {/each}
  </nav>

  <slot />

  <!-- document.body.insertAdjacentHTML("afterbegin", ` -->
  <label class="color-scheme">
      Theme:
      <select bind:value={ colorScheme }>
      <option value= "light dark" >Automatic</option>
      <option value="light" >Light</option>
      <option value="dark">Dark</option>
      </select>
  </label>
<!-- ); -->


<style>

.color-scheme {
  position: absolute; /* Take the switcher out of the normal document flow */
  top: 1rem; /* Distance from the top edge of the document */
  right: 1rem; /* Distance from the right edge of the document */
  font-size: 80%; /* Make the font a bit smaller */
}


</style>

