<article>
    <svelte:element this={"h" + hLevel}>{ data.title }</svelte:element>
    <img src={data.image} alt="">
    <p>{data.description}</p>
    <div>c. {data.year}</div>
  </article>


  <script>
    export let data = {};
    export let hLevel = 2;
  </script>

