<script lang="ts">
	export let skill: { name: string; level: number };
	export let delay: number = 0;
</script>

<div class="skill-badge" style="--delay: {delay}ms; --level: {skill.level}%">
	<span class="skill-name">{skill.name}</span>
	<div class="skill-level">
		<div class="skill-bar"></div>
	</div>
</div>

<style>
	.skill-badge {
		background: rgba(180, 190, 254, 0.1);
		border: 1px solid rgba(180, 190, 254, 0.3);
		border-radius: var(--radius-lg);
		padding: var(--spacing-sm) var(--spacing-md);
		position: relative;
		overflow: hidden;
		opacity: 0;
		transform: scale(0.9);
		animation: popIn 0.5s ease forwards;
		animation-delay: var(--delay);
		transition: all 0.3s ease;
	}
	
	.skill-badge:hover {
		background: rgba(180, 190, 254, 0.2);
		border-color: var(--lavender);
		transform: translateY(-2px);
		box-shadow: 0 4px 12px rgba(180, 190, 254, 0.3);
	}
	
	.skill-name {
		font-weight: 600;
		font-size: 0.9rem;
		color: var(--text);
		position: relative;
		z-index: 2;
	}
	
	.skill-level {
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		height: 3px;
		background: rgba(180, 190, 254, 0.2);
		overflow: hidden;
	}
	
	.skill-bar {
		height: 100%;
		width: var(--level);
		background: linear-gradient(90deg, var(--lavender), var(--mauve));
		transform: scaleX(0);
		transform-origin: left;
		animation: fillBar 1s ease forwards;
		animation-delay: calc(var(--delay) + 300ms);
	}
	
	@keyframes popIn {
		to {
			opacity: 1;
			transform: scale(1);
		}
	}
	
	@keyframes fillBar {
		to {
			transform: scaleX(1);
		}
	}
</style>