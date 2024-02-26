<script>
	import Section from './Section.svelte';
	import ContactItem from './ContactItem.svelte';
	export let sections;
</script>

<div id="side-column">
	{#each sections as { label, details, type }}
		<Section {label} {details} {type}></Section>

		{#if type === 'contact'}
		{#each details as detail}
		  <ContactItem {detail} />
	{/each}

	    <!-- Your contact form markup goes here -->
		<div class="contact-form">
			<h2>Contact Me</h2>
			<!-- Your form goes here -->
		  </div>
		{/if}
	  {/each}
</div>

<style>
	#side-column {
		width: calc(100% - var(--main-column-width));
		margin: 0 var(--horizontal-space-between-columns);
		text-align: var(--more-centered);
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}
</style>