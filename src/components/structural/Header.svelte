<script>
	export const name = 'Visakh Radhakrishnan';
	const summaryLines = [
		'Solution driven analyst with over 2 years of experience in the digital business domain. Looking for a CDI in the data domain starting September 2023.',
	];
	
</script>

<style>
	#header {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: space-between;
		text-align: center;
		margin-bottom: var(--vertical-space-between-sections);
		background-color: black; /* Set background color to black */
        color: white; /* Set text color to white */
		position: relative;
	}

	#my-name {
		text-transform: uppercase;
		color: var(--accent-color);
		font-family: var(--accent-font);
		font-size: 3em;
		margin: 0;
		position: relative;
	}

	#my-name:hover::after {
		content: '';
		position: absolute;
		top: 100;
		right: 100%;
		width: 100%;
		height: 100%;
		border: 2px solid blue; /* Change border color to blue */
		z-index: -1;

	}

	.summary {
		width: 78%;
		margin-top: 5px;
		font-size: 1.05em;
		font-weight: 300;
		font-family: var(--accent-font);
		line-height: 1.5em;
		color: white;
	}

	#header:hover {
        color: orange; /* Change text color to blue on hover */
        cursor: pointer; /* Change cursor on hover */
    }

</style>

<div id="header">
	<h1 id="my-name">{name}</h1>
	<div class="summary">
		{#each summaryLines as line, i}
			<div class="summary-line-{i}">
				{@html line}
			</div>
		{/each}
	</div>
</div>
