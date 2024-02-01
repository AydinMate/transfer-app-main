<script lang="ts">
	import googleIcon from '$lib/images/google-icon.png';
	export let type: string;
</script>

<div
	class="flex flex-col bg-tertiary-50 rounded items-center h-[35rem] px-10 w-[30rem] justify-start pt-[4rem] m-4"
>
	<div class="mb-4 flex w-full justify-between">
		<a class="w-[49%]" href="/login"
			><button
				class="h3 font-bold btn {type === 'login'
					? 'variant-filled-primary'
					: 'variant-outline-primary text-surface-900 hover:text-surface-500'} rounded py-4 w-full"
			>
				Log In
			</button></a
		>
		<a class="w-[49%]" href="/signup">
			<button
				class="h3 font-bold btn {type === 'signup'
					? 'variant-filled-primary'
					: 'variant-outline-primary text-surface-900 hover:text-surface-500'} rounded py-4 w-full"
			>
				Sign up
			</button></a
		>
	</div>
	<div class="flex flex-col space-y-4 w-full">
		<input class="bg-tertiary-50" type="email" placeholder="Email Address" />
		<input class="bg-tertiary-50" type="password" placeholder="Password" />
		<div class="h-12 flex flex-col justify-center">
			{#if type === 'login'}
				<a href="/forgot">
					<p class="text-primary-700 hover:text-primary-500">Forgot password?</p>
				</a>
			{:else}
				<input class="bg-tertiary-50 w-full" type="password" placeholder="Repeat Password" />
			{/if}
		</div>
		<button class="btn variant-filled-primary rounded font-bold py-4 text-lg"
			>{type === 'login' ? 'Log In' : 'Sign Up'}</button
		>

		<a href="/">
			<button
				class="flex flex-row space-x-4 justify-center items-center w-full bg-tertiary-300 hover:bg-tertiary-200 py-4"
			>
				<img class="w-6 h-6" src={googleIcon} alt="google-icon" />
				<p class="text-surface-900 font-bold text-lg">
					{type === 'login' ? 'Log in with Google' : 'Sign up with Google'}
				</p></button
			>
		</a>

		<p class="text-surface-900">
			{#if type === 'login'}
				Don't have an account? <a href="/signup" class="text-primary-700 hover:text-primary-500"
					>Sign up</a
				>
			{:else}
				Already have an account? <a href="/login" class="text-primary-700 hover:text-primary-500"
					>Log In</a
				>
			{/if}
		</p>
	</div>
</div>

<style>
	input {
		border-radius: 0.25rem;
		padding: 0.75rem 0.5rem;
	}
</style>
