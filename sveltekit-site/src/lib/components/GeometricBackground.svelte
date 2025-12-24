<script lang="ts">
	import { onMount } from 'svelte';

	let canvas: HTMLCanvasElement;
	let animationId: number;

	interface Particle {
		x: number;
		y: number;
		vx: number;
		vy: number;
		size: number;
		colorIndex: number;
		alpha: number;
	}

	// Enhanced purple/teal color palette
	const particleColors = [
		{ r: 169, g: 137, b: 245 }, // Purple 200
		{ r: 111, g: 218, b: 201 }, // Teal 200
		{ r: 119, g: 89, b: 194 },  // Purple 300
		{ r: 16, g: 177, b: 177 },  // Teal 300
	];

	onMount(() => {
		const ctx = canvas.getContext('2d');
		if (!ctx) return;

		const setCanvasSize = () => {
			canvas.width = window.innerWidth;
			canvas.height = window.innerHeight;
		};

		setCanvasSize();

		const particles: Particle[] = [];
		const particleCount = 60;
		const connectionDistance = 180;
		const mouseInfluence = 100;

		let mouseX = -1000;
		let mouseY = -1000;

		// Track mouse position
		const handleMouseMove = (e: MouseEvent) => {
			mouseX = e.clientX;
			mouseY = e.clientY;
		};

		window.addEventListener('mousemove', handleMouseMove);

		// Create particles
		for (let i = 0; i < particleCount; i++) {
			particles.push({
				x: Math.random() * canvas.width,
				y: Math.random() * canvas.height,
				vx: (Math.random() - 0.5) * 0.4,
				vy: (Math.random() - 0.5) * 0.4,
				size: Math.random() * 2 + 1,
				colorIndex: i % particleColors.length,
				alpha: Math.random() * 0.5 + 0.3
			});
		}

		function animate() {
			ctx!.clearRect(0, 0, canvas.width, canvas.height);

			// Update and draw particles
			particles.forEach((particle, i) => {
				// Mouse interaction - particles move away from cursor
				const dx = mouseX - particle.x;
				const dy = mouseY - particle.y;
				const dist = Math.sqrt(dx * dx + dy * dy);

				if (dist < mouseInfluence) {
					const force = (mouseInfluence - dist) / mouseInfluence;
					particle.vx -= (dx / dist) * force * 0.02;
					particle.vy -= (dy / dist) * force * 0.02;
				}

				// Apply velocity with damping
				particle.x += particle.vx;
				particle.y += particle.vy;
				particle.vx *= 0.99;
				particle.vy *= 0.99;

				// Bounce off edges with padding
				if (particle.x < 0) {
					particle.x = 0;
					particle.vx *= -1;
				}
				if (particle.x > canvas.width) {
					particle.x = canvas.width;
					particle.vx *= -1;
				}
				if (particle.y < 0) {
					particle.y = 0;
					particle.vy *= -1;
				}
				if (particle.y > canvas.height) {
					particle.y = canvas.height;
					particle.vy *= -1;
				}

				// Draw particle with glow effect
				const color = particleColors[particle.colorIndex];
				ctx!.beginPath();
				ctx!.arc(particle.x, particle.y, particle.size, 0, Math.PI * 2);
				ctx!.fillStyle = `rgba(${color.r}, ${color.g}, ${color.b}, ${particle.alpha})`;
				ctx!.fill();

				// Draw connections with gradient
				for (let j = i + 1; j < particles.length; j++) {
					const other = particles[j];
					const cdx = particle.x - other.x;
					const cdy = particle.y - other.y;
					const distance = Math.sqrt(cdx * cdx + cdy * cdy);

					if (distance < connectionDistance) {
						const opacity = 0.15 * (1 - distance / connectionDistance);

						// Create gradient line
						const gradient = ctx!.createLinearGradient(
							particle.x, particle.y, other.x, other.y
						);

						const color1 = particleColors[particle.colorIndex];
						const color2 = particleColors[other.colorIndex];

						gradient.addColorStop(0, `rgba(${color1.r}, ${color1.g}, ${color1.b}, ${opacity})`);
						gradient.addColorStop(1, `rgba(${color2.r}, ${color2.g}, ${color2.b}, ${opacity})`);

						ctx!.beginPath();
						ctx!.moveTo(particle.x, particle.y);
						ctx!.lineTo(other.x, other.y);
						ctx!.strokeStyle = gradient;
						ctx!.lineWidth = 0.5;
						ctx!.stroke();
					}
				}
			});

			animationId = requestAnimationFrame(animate);
		}

		animate();

		// Handle resize
		const handleResize = () => {
			setCanvasSize();
		};

		window.addEventListener('resize', handleResize);

		return () => {
			cancelAnimationFrame(animationId);
			window.removeEventListener('resize', handleResize);
			window.removeEventListener('mousemove', handleMouseMove);
		};
	});
</script>

<canvas bind:this={canvas} class="geometric-bg"></canvas>

<style>
	.geometric-bg {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		z-index: -1;
		opacity: 0.4;
		pointer-events: none;
	}
</style>
