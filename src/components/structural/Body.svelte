<script>
	import SideColumn from './SideColumn.svelte';
	import MainColumn from './MainColumn.svelte';
	import { onMount } from 'svelte';
	import Button from './Button.svelte';
	import { readable } from 'svelte/store';

	let animateFade = false;
	let scrollY = 0;

	onMount(() => {
    // Check if user has previously set dark mode preference
    const savedDarkMode = localStorage.getItem('darkMode');
    if (savedDarkMode !== null) {
      darkMode = savedDarkMode === 'true';
    } else {
      // If no preference set, use prefers-color-scheme media query
      darkMode = window.matchMedia('(prefers-color-scheme: dark)').matches;
    }

    updateBodyClass();

	    // Listen for scroll events
		window.addEventListener('scroll', handleScroll);

// Cleanup scroll event listener on component destruction
return () => {
  window.removeEventListener('scroll', handleScroll);
};

  });

  const updateBodyClass = () => {
    document.body.classList.toggle('dark-mode', darkMode);
  };

  const handleScroll = () => {
    scrollY = window.scrollY;

    // Add logic to trigger animations based on scroll position
    // Example: If you want to add animations when you scroll past certain elements
    // if (scrollY > someThreshold) {
    //   // Apply animations or class changes
    // }

	    // Log scroll position to console for debugging
		console.log('Scroll position:', scrollY);

	// Example: Apply fadeIn animation to an element when scrolling past a certain threshold
    const thresholdElement = document.getElementById('someElementId');

    if (thresholdElement && scrollY > thresholdElement.offsetTop) {
      thresholdElement.style.opacity = 1; // Make element visible
      thresholdElement.style.transition = 'opacity 0.5ss ease-in'; // Add a smooth transition
    }
  }; 

	export const sideColumn = [
		{
			type: 'contact',
			label: 'Contact',
			details: [
				{
					contactDetails: [
						{
							isLink: true,
							type: 'email',
							text: 'visakh.radhakrishnan@essec.edu',
							icon: 'email',
						},
						{
							isLink: true,
							type: 'phone',
							text: '+330755442925',
							icon: 'phone',
						},
						{
							text: 'Cergy, Paris',
							icon: 'location',
						},
					],
				},
				{
					subcategory: 'Find me online',
					contactDetails: [
						{
							isLink: true,
							type: 'web',
							url: 'https://github.com/visakhr1998',
							text: 'github.com/visakhr1998',
							icon: 'github',
						},
						{
							isLink: true,
							type: 'web',
							url: 'https://www.linkedin.com/in/visakhr1998/',
							text: 'linkedin.com/in/visakhr1998',
							icon: 'linkedin',
						},
					],
				},
			],
		},
		{
			type: 'skills',
			label: 'Skills',
			details: [
				'PowerBI',
				'MS Office',
				'Python',
				'Tableau',
				'SQL',
				'BigQuery',
				'JIRA',
				'HTML',
				'CSS'
			],
		},
		
		{
			type: 'skills',
			label: 'Languages',
			details: [
				'French',
				'English',
				'Malayalam',
				'Hindi',
				'Tamil'
			],
		},

		
	];
	export const mainColumn = [
		{
			type: 'full-details',
			label: 'Experience',
			details: [
				{
					title: 'Data Project Manager Apprentice',
					subtitle: 'L’Oréal',
					dates: `Oct 2023 — Present`,
					location: 'Paris, FR',
					list: [
						'•	Development of a tool to track consumer complaints information using Python and Power BI to integrate insights for improved data analysis.',
						'•	Drive process efficiency by optimizing various manual tasks through Power Automate and Power Platform tools.',
						'•	Product owner for 4 BIs in the L’oreal Luxe Dev team – ensure functionality, animate training and collect user needs for continuous improvement.',
					],
				},
				{
					title: 'Proxy Product Owner Apprentice',
					subtitle: 'L’Oréal',
					dates: 'Sept 2022 — Oct 2023',
					location: 'Paris, FR',
					description: 'ELIXPEDIA (Product Master Data tool)',
					list: [
						'•	Investigated pain points to implement process changes, proposals, and new attributes to improve product quality.',
						'•	Documented global guidelines and best practices for effective communication of business processes.',
						'•	Aligned team to agile methods and took up ownership of tasks in regular sprint cycles as an agile practitioner.',
,
					],
				},
				{
					title: 'Data Analyst Intern',
					subtitle: 'Schneider Electric',
					dates: 'April 2022 - Sep 2022',
					location: 'Paris, FR',
					list: [
						'•	Built dashboards using Tableau to analyze the progress of defect rates and quality costs in Schneider factories leading to an annual saving of 3.2M€ ',
						'•	Deployed e-tools to digitize the traceability of the end-to-end supply chain for over 200 plants in Asia',
					],
				},
				{
					title: 'Accenture',
					subtitle: 'External Consultant',
					dates: 'January 2022 - May 2022',
					location: 'Paris, FR',
					description: 'External Consultant for Dataiku, a B2B SaaS platform',
					list: [
						'•	Analyzed customer data on product usage and the sales cycle for 1000+ companies interacting with Dataiku',
						'•	Identified key customer pain points and formulated strategies for the sales team to target customers effectively through lowering the preparation time by 40%',
,
					],
				},
			],
		},
		{
			type: 'full-details',
			label: 'Education',
			details: [
				{
					title: 'Masters in Management',
					subtitle: 'ESSEC Business School',
					description: 'GPA: 16.7/20',
					dates: '2021 - Present',
					location: 'Paris, FR',
				},
				{
					title: 'Bachelor of Technology',
					subtitle: 'NIT Calicut',
					description: 'GPA: 9.15/10',
					dates: '2015-2019',
					location: 'Calicut, IN',
				},
			],
		},
	];
</script>

<style>
		:global(body) {
		background-color: #fff;
		color: #000;
		transition: background-color 0.3s
	}

	:global(body.dark-mode) {
		background-color: #1d3040;
		color: #bfc2c7;
	}

	div {
		display: flex;
		justify-content: space-between;
		flex-direction: var(--column-order);
		margin: 0 var(--horizontal-offset);
	}

	.animate-fade {
    transition: opacity 2s cubic-bezier(0.35, 0.5, 0.65, 0.95);
  }

  /* Initially set opacity to 0 for the fade-in effect */
  .fade-initial {
    opacity: 0;
  }

</style>

<Button />

<div class="main-body">
    <MainColumn sections={mainColumn} />
    <SideColumn sections={sideColumn} />
</div>
