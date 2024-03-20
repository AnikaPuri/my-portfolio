<script>

import * as d3 from 'd3';

export let data = [];


let arcGenerator = d3.arc().innerRadius(0).outerRadius(50);

let arc = arcGenerator({
	startAngle: 0,
	endAngle: 2 * Math.PI
});

let sliceGenerator = d3.pie().value(d => d.value);

// Make sure the variable definition is *outside* the block
let arcData; 
let arcs;

$: {
	// Initialize to an empty object every time this runs
	arcData = sliceGenerator(data);
    arcs = arcData.map(d => arcGenerator(d));

	// Calculate rolledData and pieData based on filteredProjects here
}


let colors = d3.scaleOrdinal(d3.schemePastel1);

export let selectedIndex = -1;


</script>


<div class = "container">
    <svg viewBox="-50 -50 100 100">
        {#each arcs as arc, index}
        
	<path d={arc} fill={ colors(index) }
        class:selected={selectedIndex === index}
	      on:click={e => selectedIndex = selectedIndex === index ? -1 : index
	      } />
{/each}
    </svg> 
 
    <ul class="legend">
      {#each data as d, index}
        <li style="--color: { colors(index) }">
          <span class="swatch"></span>
          {d.label} <em>({d.value})</em>
        </li>
      {/each}
    </ul>
</div>




<style>

.swatch {
    /* aspect-ratio: 1 /1; */
    width:1em;
    height:1em;
    background-color: var(--color);
    border-radius: 50%;
    align-items: center;
    border-spacing: gap;
    display: flex;

  }

  ul {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(9em, 1fr));
    /* max-width: 100%;  */
    outline: 0.1em solid black;
    outline-offset: 1em;
  }

  li {
    display: flex;
    gap:0.5em;;
  }

  svg {
    max-width: 20em;
    width:40vw;
    margin-block: 2em;


    /* Do not clip shapes outside the viewBox */
    overflow: visible;
  }

  .container {
    display: flex;
    align-items: center;
    gap: 4em;
    padding: 0em;
  }

  .legend {
    flex: 1
    /* list-style-type: none; */
  }

  svg:has(path:hover) {
	path:not(:hover) {
		opacity: 50%;
	}
}
path {
	transition: 300ms;
}

.selected {
	--color: oklch(60% 45% 0) !important;

	&:is(path) {
		fill: var(--color);
	}
}

  </style>