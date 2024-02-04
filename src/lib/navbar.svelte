<script>
	let logo = 'Logo';
	let links = [
		{ name: 'Home', href: '/' },
		{ name: 'About', href: '/about' },
		{ name: 'Pricing', href: '/pricing' }
	];
</script>

<nav>
	<div class="logo">
		<span>{logo}</span>
	</div>
	<div class="nav-links">
		{#each links as link}
			<a href={link.href}><button class="btn variant-filled-primary">{link.name}</button></a>
		{/each}
	</div>
	<div class="login">
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
	}

	/* .logo img {
    width: 40px;
    height: 40px;
    margin-right: 0.5rem;
  } */

	.nav-links button {
		margin-right: 1rem;
		text-decoration: none;
	}
</style>
