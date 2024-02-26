<script>
	import Section from './Section.svelte';
	import { onMount } from 'svelte';
	import Button from './Button.svelte';
	import ContactItem from './ContactItem.svelte';
  
	let sections = []; // Add your sections array here
  
	onMount(() => {
	  const handleScroll = () => {
		// Add your scroll logic here
	  };
  
	  window.addEventListener('scroll', handleScroll);
  
	  return () => {
		window.removeEventListener('scroll', handleScroll);
	  };
	});
  
	let showContactForm = true;
	let name = '';
	let email = '';
	let message = '';
  
	const isValidEmail = (email) => {
	  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
	  return emailRegex.test(email);
	};
  
	const handleSubmit = () => {
	  // Your form submission logic here
	  if (isValidEmail(email)) {
		alert(`Form submitted!\nName: ${name}\nEmail: ${email}\nMessage: ${message}`);
	  } else {
		alert('Invalid email address. Please provide a valid email.');
	  }
	};
  </script>
  
  <style>
	/* Add your styles here */
  </style>
  
  <Button />
  
  <div class="main-body">
	<div id="main-column">
	  {#each sections as { label, details, type }}
		<Section {label} {details} {type}></Section>
	  {/each}
	</div>
  
	<div id="side-column">
		{#each sections as { label, details, type }}
		  <Section {label} {details} {type}></Section>
	  
		  {#if type === 'contact'}
			  <ContactItem {detail} />
			{#if showContactForm}
			  <!-- Your contact form markup goes here -->
			  <div class="contact-form">
				<h2>Contact Me</h2>
				<form on:submit|preventDefault={handleSubmit}>
				  <label for="name">Name:</label>
				  <input type="text" id="name" bind:value={name} required />
	  
				  <label for="email">Email:</label>
				  <input type="email" id="email" bind:value={email} required />
	  
				  <label for="message">Message:</label>
				  <textarea id="message" bind:value={message} required></textarea>
	  
				  <button type="submit">Submit</button>
				</form>
			  </div>
			{/if}
		  {/if}
		{/each}
	  </div>
  </div>
  