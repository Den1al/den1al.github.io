<script lang="ts">
	const year = new Date().getFullYear();
</script>

<footer>
	<div class="container">
		<p>&copy; {year} Daniel Abeles. All rights reserved.</p>
		<p class="email">
			<a href="mailto:hello@abeles.dev">hello@abeles.dev</a>
		</p>
	</div>
</footer>

<style>
	footer {
		position: relative;
		background: linear-gradient(
			180deg,
			var(--bg-secondary) 0%,
			var(--bg-primary) 100%
		);
		padding: var(--spacing-2xl) 0 var(--spacing-xl);
		margin-top: var(--spacing-3xl);
		text-align: center;
	}

	/* Gradient top border */
	footer::before {
		content: '';
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		height: 1px;
		background: linear-gradient(
			90deg,
			transparent,
			var(--purple-01p),
			var(--teal-03s),
			var(--purple-01p),
			transparent
		);
		opacity: 0.4;
	}

	footer p {
		margin-bottom: var(--spacing-xs);
		color: var(--text-muted);
		font-size: 0.9rem;
	}

	.email {
		margin-top: var(--spacing-sm);
	}

	.email a {
		color: var(--teal-02s);
		font-weight: 500;
		position: relative;
		transition: all var(--transition-normal);
	}

	.email a::after {
		content: '';
		position: absolute;
		bottom: -2px;
		left: 0;
		width: 100%;
		height: 2px;
		background: var(--teal-03s);
		transform: scaleX(0);
		transition: transform var(--transition-normal);
	}

	.email a:hover {
		color: var(--teal-01s);
	}

	.email a:hover::after {
		transform: scaleX(1);
	}
</style>