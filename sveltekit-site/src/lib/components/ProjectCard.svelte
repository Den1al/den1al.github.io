<script lang="ts">
	export let project: {
		name: string;
		url: string;
		description: string;
		tagline: string;
	};
</script>

<article class="project-card">
	<h3><a href={project.url} target="_blank" rel="noopener">{project.name}</a></h3>
	<p class="tagline">{project.tagline}</p>
	<blockquote class="description">
		{project.description}
	</blockquote>
</article>

<style>
	.project-card {
		position: relative;
		background: var(--surface-glass);
		backdrop-filter: blur(16px) saturate(180%);
		-webkit-backdrop-filter: blur(16px) saturate(180%);
		border: 1px solid var(--surface-glass-border);
		border-radius: var(--radius-lg);
		padding: var(--spacing-lg);
		height: 100%;
		display: flex;
		flex-direction: column;
		transition: all var(--transition-slow);
		overflow: hidden;
	}

	/* Gradient border effect on hover */
	.project-card::before {
		content: '';
		position: absolute;
		inset: -1px;
		border-radius: calc(var(--radius-lg) + 1px);
		background: linear-gradient(
			135deg,
			transparent 0%,
			var(--purple-01p) 50%,
			var(--teal-03s) 100%
		);
		opacity: 0;
		z-index: -1;
		transition: opacity var(--transition-slow);
	}

	/* Corner teal accent glow */
	.project-card::after {
		content: '';
		position: absolute;
		top: 0;
		right: 0;
		width: 60px;
		height: 60px;
		background: radial-gradient(
			circle at top right,
			rgba(16, 177, 177, 0.15) 0%,
			transparent 70%
		);
		transition: all var(--transition-slow);
	}

	.project-card:hover {
		background: var(--surface-glass-hover);
		transform: translateY(-8px);
		box-shadow:
			var(--shadow-xl),
			var(--shadow-glow-purple);
	}

	.project-card:hover::before {
		opacity: 1;
	}

	.project-card:hover::after {
		width: 100px;
		height: 100px;
		background: radial-gradient(
			circle at top right,
			rgba(16, 177, 177, 0.25) 0%,
			transparent 70%
		);
	}

	.project-card h3 {
		margin-bottom: var(--spacing-sm);
		position: relative;
		z-index: 1;
	}

	.project-card h3 a {
		color: var(--purple-01p);
		text-decoration: none;
		transition: color var(--transition-normal);
	}

	.project-card h3 a:hover {
		color: var(--teal-02s);
	}

	.tagline {
		font-weight: 600;
		color: var(--text-tertiary);
		margin-bottom: var(--spacing-md);
		font-size: 0.95rem;
		position: relative;
		z-index: 1;
	}

	.description {
		flex: 1;
		font-size: 0.9rem;
		margin: 0;
		border-left: 3px solid var(--teal-03s);
		padding-left: var(--spacing-md);
		color: var(--text-tertiary);
		background: transparent;
		border-radius: 0;
		font-style: normal;
		position: relative;
		z-index: 1;
	}
</style>