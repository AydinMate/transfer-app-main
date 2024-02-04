<script lang="ts">
	import googleIcon from '$lib/images/google-icon.svg';
    import appleIcon from '$lib/images/apple-icon.svg';
	import { supabase } from './supabase-client';

	export let type: string;
	export let provider: string;

	const signInWithGoogle = async () => {
		await supabase.auth.signInWithOAuth({
			provider: 'google',
			options: {
				redirectTo: '/dashboard'
			}
		});
	};
</script>

<button
	on:click={provider === 'google' ? signInWithGoogle : null}
	class="flex flex-row space-x-4 justify-center items-center w-full bg-tertiary-300 hover:bg-tertiary-200 py-4"
>
	<img
		class="w-6 h-auto"
		src={provider === 'google' ? googleIcon : appleIcon}
		alt={`${provider === 'google' ? 'Google' : 'Apple'}-icon`}
	/>
	<p class="text-surface-900 font-bold text-lg">
		{type === 'login'
			? `Log in with ${provider === 'google' ? 'Google' : 'Apple'}`
			: `Sign up with ${provider === 'google' ? 'Google' : 'Apple'}`}
	</p></button
>
