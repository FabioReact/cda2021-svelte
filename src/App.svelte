<script>
	import ListItem from './ListItem.svelte'
	import Form from './Form.svelte'
	export let name
	export let city
	let visible = false
	let activePage = 'home'
	const prenom = "Fabio"
	const src = 'https://www.avoir-alire.com/IMG/arton42400.png'
	const alt = 'Affiche de la série La casa de papel'
	const results = [
		{
			id: 1,
			title: "Uprising",
			artist: "Muse",
		},
		{
			id: 2,
			title: "Bohemian Rapsody",
			artist: "Muse",
		},
		{
			id: 3,
			title: "Billie Jean",
			artist: "Michael Jackson",
		},
		{
			id: 4,
			title: "Taki taki",
			artist: "Dj Snake",
		},
	]
	const handleClick = () => {
		visible = !visible
	}
</script>

<nav>
	<li><a href="/" on:click|preventDefault={() => activePage = 'home'}>Home</a></li>
	<li><a href="/" on:click|preventDefault={() => activePage = 'form'}>Form</a></li>
	<li><a href="/" on:click|preventDefault={() => activePage = 'musicList'}>Music List</a></li>
</nav>
<main>
	{#if activePage === 'home'}
		<h1>Hello {name}!</h1>
		<p>Hello {prenom} from {city}</p>
		<img {src} {alt}>
	{:else if activePage === 'form'}
		<Form />
	{:else if activePage === 'musicList'}
		<button on:click={handleClick}>Afficher/Masquer la liste</button>
		{#if visible}
			{#each results as result (result.id)}
				<ListItem song={result.title} artist={result.artist} />
			{/each}
		{/if}
	{/if}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	img {
		display: block;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>