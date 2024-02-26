<script>
	import { readable } from 'svelte/store';
	import Contact from '../sections/Contact.svelte';
	import Skills from '../sections/Skills.svelte';
	import FullDetails from '../sections/FullDetails.svelte';
	import SimpleDetails from '../sections/SimpleDetails.svelte';
  
	export let label;
	export let details;
	export let type;
  
	let scrollY = readable(0, set => {
	  const handleScroll = () => {
		set(window.scrollY); 	
	  };
  
	  window.addEventListener('scroll', handleScroll);
  
	  return () => {
		window.removeEventListener('scroll', handleScroll);
	  };
	});
  
	const animationThreshold = 200; // Adjust as needed
  </script>
  
  <style>
	.section-box {
	  background-color: #f4f4f4;
	  padding: 10px;
	  margin-bottom: 15px;
	  border-radius: 8px;
	  opacity: 0.5;
	  transition: opacity 2s cubic-bezier(0.35, 0.5, 0.65, 0.95);
	}
  
	.animate-fade {
	  opacity: 1;
	}
  
	.section-label {
	  margin: 0;
	}
  </style>
  
  <div class="section-box animate-fade">
	<h2 class="section-label">{label}</h2>
	<hr class="section-underline" />
  
	{#if type === 'simple-details'}
	  <SimpleDetails {label} {details} />
	{:else if type === 'full-details'}
	  <FullDetails {label} {details} />
	{:else if type === 'skills'}
	  <Skills {label} {details} />
	{:else if type === 'contact'}
	  <Contact {label} {details} />
	{/if}
  </div>
  