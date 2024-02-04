<script lang="ts">
	import OauthButton from './oauth-button.svelte';
	import { supabase } from './supabase-client';
	export let type: string;

	let firstPassword: string = "";
	let secondPassword: string = "";
	let passwordsMatch = false;

	$: passwordsMatch = firstPassword === secondPassword && firstPassword.length > 8 && /[A-Z]/.test(firstPassword) && /\d/.test(firstPassword);

	let passwordInputClass = "";
	$: {
		if (!passwordsMatch && (firstPassword.length > 0 || secondPassword.length > 0) && type === 'signup') {
			passwordInputClass = "border-error-500 border-2";
		} else if (passwordsMatch) {
			passwordInputClass = "border-success-500 border-2";
		} else {
			passwordInputClass = "";
		}
	}
</script>

<div
	class="flex flex-col bg-tertiary-50 rounded items-center px-10 w-[30rem] justify-start pt-[3.5rem] pb-[2rem] m-4"
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
		<input class="bg-tertiary-50 text-surface-900" type="email" placeholder="Email Address" />
		<input class="bg-tertiary-50 text-surface-900 {passwordInputClass}" type="password" placeholder="Password" bind:value={firstPassword}/>
		<div class="h-12 flex flex-col justify-center">
			{#if type === 'login'}
				<a href="/forgot">
					<p class="text-primary-700 hover:text-primary-500">Forgot password?</p>
				</a>
			{:else}
				<input class="bg-tertiary-50 w-full text-surface-900 {passwordInputClass}" type="password" placeholder="Repeat Password" bind:value={secondPassword}/>
			{/if}
		</div>
		<button class="btn variant-filled-primary rounded font-bold py-4 text-lg"
			>{type === 'login' ? 'Log In' : 'Sign Up'}</button
		>
		<OauthButton {type} provider={"apple"}/>
		<OauthButton {type} provider={"google"}/>
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
