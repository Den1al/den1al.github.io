<script lang="ts">
	import { onMount } from 'svelte';
	
	export let text: string;
	export let speed: number = 100;
	
	let displayText = '';
	let currentIndex = 0;
	
	onMount(() => {
		const typeWriter = () => {
			if (currentIndex < text.length) {
				displayText += text.charAt(currentIndex);
				currentIndex++;
				setTimeout(typeWriter, speed);
			}
		};
		
		typeWriter();
	});
</script>

<span class="typewriter">
	{displayText}
	<span class="cursor">|</span>
</span>

<style>
	.typewriter {
		font-family: 'Fira Code', monospace;
	}
	
	.cursor {
		animation: blink 1s infinite;
		color: var(--green);
	}
	
	@keyframes blink {
		0%, 50% { opacity: 1; }
		51%, 100% { opacity: 0; }
	}
</style>