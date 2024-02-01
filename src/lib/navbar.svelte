<script>

	let logo = 'Logo';
    let links = [
        { name: 'Home', href: '/' },
        { name: 'About', href: '/about' },
        { name: 'Pricing', href: '/pricing' },
    ];
</script>

<nav>
	<div class="logo">
		<!-- <img src="path/to/logo.png" alt="Logo" /> -->
		<span>{logo}</span>
	</div>
	<div class="nav-links">
        {#each links as link}
            <button class="btn variant-filled-primary"><a href={link.href}>{link.name}</a></button>
        {/each}
	</div>
	<div class="login">
		<button class="btn variant-filled-secondary">
            <a href="/login">Login</a>
        </button>
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
