<svelte:head>
	<title>Contact me</title>
</svelte:head>
<h1>Contact ME</h1>
<form action="mailto:anpuri@mit.edu" method="post" enctype = "text/plain">
      <label for="email">Email: </label>
      <input type="email" name="email" id="email" required />
      <label for="subject">Subject: </label>
      <input type="text" name="subject" id="subject" required />
      <label for="body">Body:</label>
      <textarea id="body" name="body" rows="5" cols="33"></textarea>
      <button type="submit">Submit</button>
  </form>