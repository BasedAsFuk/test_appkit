<script>
	import { onMount } from 'svelte';
	import { PUBLIC_PROJECT_ID } from '$env/static/public';

	import { createAppKit } from '@reown/appkit/react'
	import { SolanaAdapter } from '@reown/appkit-adapter-solana/react'
	import { solana, solanaTestnet, solanaDevnet } from '@reown/appkit/networks'
	//import { PhantomWalletAdapter, SolflareWalletAdapter } from '@solana/wallet-adapter-wallets'

	import { page } from '$app/stores';


async function initalizeSolanaAdapter(){
	// 0. Set up Solana Adapter
	const solanaWeb3JsAdapter = new SolanaAdapter({
		//wallets: [new PhantomWalletAdapter(), new SolflareWalletAdapter()]
	})

	// 1. Get projectId from https://cloud.reown.com
	const projectId = PUBLIC_PROJECT_ID

	// 2. Create a metadata object - optional
	const metadata = {
		name: 'AppKit',
		description: 'AppKit Solana Example',
		url: $page.url.origin, // origin must match your domain & subdomain
		icons: ['https://avatars.githubusercontent.com/u/179229932']
	}

	// 3. Create modal
	createAppKit({
		adapters: [solanaWeb3JsAdapter],
		networks: [solana, solanaTestnet, solanaDevnet],
		metadata: metadata,
		projectId,
		features: {
			analytics: true // Optional - defaults to your Cloud configuration
		}
	})
}

onMount(() => {
	initalizeSolanaAdapter()
})

</script>


<h1>Welcome to AppKit Test on Sveltekit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
<w3m-button></w3m-button>