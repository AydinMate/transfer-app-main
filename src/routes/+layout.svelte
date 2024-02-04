<script lang="ts">
	import { goto } from '$app/navigation';
	import Navbar from '$lib/navbar.svelte';
	import { supabase } from '$lib/supabase-client';
	import '../app.postcss';

	// Floating UI for Popups
	import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';
	import { storePopup } from '@skeletonlabs/skeleton';
	storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });
    

</script>

<Navbar />
<slot />

