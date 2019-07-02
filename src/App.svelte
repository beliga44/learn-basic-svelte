<script>
	import Header from './Header.svelte';
	import DrafterForm from './DrafterForm.svelte';
	import { fade } from 'svelte/transition';

	let visibleForm = false;

	let drafters = [
		{
			name: 'Udin Sumitro',
			height: 180,
			team: 'Utah Jazz',
			position: 'PG',
			college_country: 'Utah'
		},
		{
			name: 'Sum Sabolaga',
			height: 203,
			team: 'Sacramento Kings',
			position: 'C',
			college_country: 'Canada'
		}
	];

	function onAddDrafter(event) {
		let drafter = event.detail;
		drafters = [...drafters, drafter];
	};

	function handleFormView(event) {
		event.preventDefault();

		visibleForm = !visibleForm;
	}
</script>

<Header/>
<div class="container mt-3">
	<button on:click={handleFormView} type="button" class="btn btn-outline-primary">Add New Drafter</button>
	{#if visibleForm}
	<button on:click={handleFormView} type="button" class="btn btn-outline-danger">Cancel</button>
	<div class="fluid-container mt-3" transition:fade>
		<DrafterForm on:add_drafter={onAddDrafter}/>
	</div>
	{/if}
	<div class="card-deck">
		{#each drafters as drafter}
		<div class="card mt-3" style="width: 18rem;">
			<div class="card-body">
				<h5 class="card-title">{drafter.name}</h5>
				<h6 class="card-subtitle mb-2 text-muted">{drafter.height}cm - {drafter.team}</h6>
				<p class="card-text">Position: {drafter.position} from {drafter.college_country}</p>
			</div>
		</div>
		{/each}
	</div>
</div>
