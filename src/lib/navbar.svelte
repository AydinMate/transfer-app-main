<script>
import Logo from './images/logo.svelte';
	let links = [
		{ name: 'Home', href: '/' },
		{ name: 'About', href: '/about' },
		{ name: 'Pricing', href: '/pricing' }
	];
</script>

<nav>
	<a href="/" class="logo z-20">
		<Logo styles="fill-current text-surface-50 hover:text-surface-200 hover:cursor-pointer transition-colors duration-200" />
	</a>
	<div class="nav-links space-x-4 w-full absolute left-0 justify-center items-center flex z-10">
		{#each links as link}
			<a href={link.href}><button class="btn variant-filled-primary nav-button ">{link.name}</button></a>
		{/each}
	</div>
	<div class="login z-20">
		<a href="/login"> <button class="btn variant-filled-secondary">Login</button></a>
	</div>
</nav>

<style>
	nav {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 1rem;
	}

	button {
		border-radius: 0.25rem;
	}

	.logo {
		display: flex;
		align-items: center;
		height: auto;
		width: 4.5rem;
	}



	.nav-button {
    text-decoration: none;
}

</style>
