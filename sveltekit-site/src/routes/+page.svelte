<script lang="ts">
	import { onMount } from 'svelte';
	import GeometricBackground from '$lib/components/GeometricBackground.svelte';

	let mounted = false;
	let activeSection = 'hero';

	const employment = [
		{ company: 'GitLab', url: 'https://gitlab.com/', years: '2024-present', position: 'Vulnerability Research Manager', current: true },
		{ company: 'Oxeye', url: 'https://www.oxeye.io/', years: '2021-2024', position: 'Head of Research', current: false },
		{ company: 'Akamai', url: 'https://www.akamai.com/', years: '2016-2021', position: 'Principal Security Research Lead', current: false },
		{ company: 'Avnet', url: 'https://www.rockwellautomation.com/', years: '2014-2016', position: 'Senior Security Researcher', current: false }
	];

	const conferences = [
		{ name: 'DC9723', year: '2025', topic: 'What Happens When Packages Start Maintaining Themselves', url: 'https://www.linkedin.com/posts/daniel-abeles_shaihulud-supplychain-security-activity-7409865175396425729-WgTY' },
		{ name: 'BlueHat IL', year: '2023', topic: 'The Story of a Backstage RCE', url: 'https://www.youtube.com/watch?v=PKUdLqLLAes' },
		{ name: 'Blackhat Arsenal', year: '2022', topic: 'Ox4Shell - Deobfuscate Log4Shell', url: 'https://www.blackhat.com/us-22/arsenal/schedule/#oxshell' },
		{ name: 'BSides Las Vegas', year: '2020', topic: 'Abusing Service Workers Web API', url: 'https://www.youtube.com/watch?v=b7V5_xnXA1U' },
		{ name: 'Blackhat Arsenal', year: '2019', topic: 'JSShell - Interactive XSS Tool', url: 'https://www.blackhat.com/us-19/arsenal/schedule/#jsshell' },
		{ name: 'Blackhat Arsenal', year: '2018', topic: 'MQTT-PWN IoT Swiss Army Knife', url: 'https://www.blackhat.com/us-18/arsenal/schedule/' }
	];

	const projects = [
		{
			name: 'Ox4Shell',
			url: 'https://github.com/ox-eye/Ox4Shell',
			description: 'Deobfuscate Log4Shell payloads with ease. Unravel the true contents of obfuscated CVE-2021-44228 payloads.',
			tagline: 'Log4Shell Deobfuscator',
			icon: '🛡️'
		},
		{
			name: 'JSShell',
			url: 'https://github.com/Den1al/JSShell',
			description: 'Interactive multi-user web-based JavaScript shell for XSS exploitation and browser debugging.',
			tagline: 'XSS Management Tool',
			icon: '💻'
		},
		{
			name: 'MQTT-PWN',
			url: 'https://github.com/akamai-threat-research/mqtt-pwn',
			description: 'One-stop-shop for IoT Broker penetration-testing with enumeration and exploitation modules.',
			tagline: 'IoT Pentesting Toolkit',
			icon: '📡'
		}
	];

	const blogPosts = [
		{ title: 'GitLab discovers widespread npm supply chain attack', url: 'https://about.gitlab.com/blog/gitlab-discovers-widespread-npm-supply-chain-attack/' },
		{ title: 'Take Me to Prom - Exploiting RCE in openTSDB through Prometheus', url: 'https://www.oxeye.io/resources/take-me-to-prom' },
		{ title: 'Gophers & Bees - Parsing Golang structures with eBPF', url: 'https://www.oxeye.io/resources/parsing-golang-structures' },
		{ title: 'RCE through SQL Injection in Hashicorp Vault', url: 'https://www.oxeye.io/resources/rce-through-sql-injection' },
		{ title: 'BreakStage - Unauthenticated RCE in Spotify Backstage', url: 'https://www.oxeye.io/resources/remote-code-execution-in-spotifys-backstage' },
		{ title: 'Sandbreak - VM2 Sandbox Escape (CVE-2022-36067)', url: 'https://www.oxeye.io/resources/vm2-sandbreak-vulnerability' },
		{ title: 'ParseThru - HTTP Parameter Smuggling in Golang', url: 'https://www.oxeye.io/resources/golang-parameter-smuggling' }
	];

	const skills = [
		'Vulnerability Research',
		'Penetration Testing',
		'Reverse Engineering',
		'Code Analysis',
		'Exploit Development',
    'Software Development',
    'PoC Ideation',
		'IoT Security',
		'Cloud Security',
		'Web Security'
	];

	// Scroll reveal logic
	onMount(() => {
		mounted = true;

		const observerOptions = {
			root: null,
			rootMargin: '0px',
			threshold: 0.1
		};

		const observer = new IntersectionObserver((entries) => {
			entries.forEach(entry => {
				if (entry.isIntersecting) {
					entry.target.classList.add('visible');
				}
			});
		}, observerOptions);

		document.querySelectorAll('.reveal, .reveal-left, .reveal-scale').forEach(el => {
			observer.observe(el);
		});

		// Section tracking for sidebar
		const sectionObserver = new IntersectionObserver((entries) => {
			entries.forEach(entry => {
				if (entry.isIntersecting) {
					activeSection = entry.target.id;
				}
			});
		}, { threshold: 0.3 });

		document.querySelectorAll('section[id]').forEach(section => {
			sectionObserver.observe(section);
		});

		return () => {
			observer.disconnect();
			sectionObserver.disconnect();
		};
	});

	// Terminal typing effect
	let terminalText = '';
	const fullText = 'daniel@abeles:~$ whoami';

	onMount(() => {
		let i = 0;
		const typeInterval = setInterval(() => {
			if (i < fullText.length) {
				terminalText = fullText.slice(0, i + 1);
				i++;
			} else {
				clearInterval(typeInterval);
			}
		}, 80);

		return () => clearInterval(typeInterval);
	});
</script>

<svelte:head>
	<title>Daniel Abeles - Security Research Leader</title>
	<meta name="description" content="Security research leader with 10+ years experience in penetration testing, reverse engineering, and vulnerability research. Currently leading GitLab's Vulnerability Research Group." />
</svelte:head>

<GeometricBackground />

<!-- Floating Side Navigation -->
<nav class="side-nav" class:mounted>
	<a href="#hero" class:active={activeSection === 'hero'} aria-label="Hero">
		<span class="nav-dot"></span>
	</a>
	<a href="#about" class:active={activeSection === 'about'} aria-label="About">
		<span class="nav-dot"></span>
	</a>
	<a href="#experience" class:active={activeSection === 'experience'} aria-label="Experience">
		<span class="nav-dot"></span>
	</a>
	<a href="#projects" class:active={activeSection === 'projects'} aria-label="Projects">
		<span class="nav-dot"></span>
	</a>
	<a href="#writing" class:active={activeSection === 'writing'} aria-label="Writing">
		<span class="nav-dot"></span>
	</a>
</nav>

<main>
	<!-- HERO SECTION -->
	<section id="hero" class="hero">
		<div class="hero-content">
			<div class="terminal-window" class:mounted>
				<div class="terminal-header">
					<span class="terminal-dot red"></span>
					<span class="terminal-dot yellow"></span>
					<span class="terminal-dot green"></span>
					<span class="terminal-title">bash</span>
				</div>
				<div class="terminal-body">
					<span class="terminal-prompt">{terminalText}</span>
					<span class="cursor">_</span>
				</div>
			</div>

			<h1 class="hero-title" class:mounted>
				<span class="title-line">Security</span>
				<span class="title-line gradient-text">Research Leader</span>
			</h1>

			<p class="hero-subtitle" class:mounted>
				Building the future of application security at <a href="https://gitlab.com" target="_blank" rel="noopener">GitLab</a>.
				10+ years breaking things to make them stronger.
			</p>

			<div class="scroll-indicator" class:mounted>
				<span class="scroll-text mono">scroll</span>
				<div class="scroll-line"></div>
			</div>
		</div>
	</section>

	<!-- ABOUT SECTION -->
	<section id="about" class="about">
		<div class="container">
			<div class="section-grid">
				<div class="section-label reveal">
					<span class="label-number">01</span>
					<span class="label-text">About</span>
				</div>

				<div class="about-content reveal delay-1">
					<blockquote class="quote">
						<span class="quote-mark">"</span>
						If I had 8 hours to chop down a tree, I would spend 6 of those hours sharpening my axe.
						<span class="quote-mark">"</span>
					</blockquote>

					<p class="about-text">
						I'm a seasoned security research leader with over a decade of experience spanning penetration testing,
						static code analysis, reverse engineering, and software development. Following Oxeye's acquisition by GitLab,
						I now lead the <strong>Vulnerability Research Group</strong>, driving the organization's security research initiatives.
					</p>

					<div class="skills-cloud">
						{#each skills as skill}
							<span class="skill-tag">{skill}</span>
						{/each}
					</div>
				</div>
			</div>
		</div>
	</section>

	<!-- EXPERIENCE SECTION - Bento Grid -->
	<section id="experience" class="experience">
		<div class="container">
			<div class="section-grid">
				<div class="section-label reveal">
					<span class="label-number">02</span>
					<span class="label-text">Experience</span>
				</div>

				<div class="bento-grid">
					<!-- Timeline Card - Large -->
					<div class="bento-card bento-large reveal delay-1">
						<h3 class="card-title">Career Timeline</h3>
						<div class="timeline">
							{#each employment as job, i}
								<div class="timeline-item" style="--index: {i}">
									<div class="timeline-marker" class:current={job.current}>
										{#if job.current}
											<span class="pulse-ring"></span>
										{/if}
									</div>
									<div class="timeline-content">
										<div class="timeline-header">
											<a href={job.url} target="_blank" rel="noopener" class="company-name">
												{job.company}
											</a>
											<span class="timeline-years mono">{job.years}</span>
										</div>
										<p class="timeline-position">{job.position}</p>
									</div>
								</div>
							{/each}
						</div>
					</div>

					<!-- Conferences Card -->
					<div class="bento-card reveal delay-2">
						<h3 class="card-title">Speaking</h3>
						<div class="conference-list">
							{#each conferences.slice(0, 4) as conf}
								<a href={conf.url} target="_blank" rel="noopener" class="conference-item">
									<span class="conf-name">{conf.name}</span>
									<span class="conf-year mono">{conf.year}</span>
								</a>
							{/each}
						</div>
					</div>

				</div>
			</div>
		</div>
	</section>

	<!-- PROJECTS SECTION -->
	<section id="projects" class="projects">
		<div class="container">
			<div class="section-grid">
				<div class="section-label reveal">
					<span class="label-number">03</span>
					<span class="label-text">Projects</span>
				</div>

				<div class="projects-showcase">
					{#each projects as project, i}
						<a
							href={project.url}
							target="_blank"
							rel="noopener"
							class="project-card reveal"
							style="--delay: {i * 0.15}s"
						>
							<div class="project-icon">{project.icon}</div>
							<div class="project-info">
								<h3 class="project-name">{project.name}</h3>
								<p class="project-tagline">{project.tagline}</p>
								<p class="project-desc">{project.description}</p>
							</div>
							<div class="project-arrow">
								<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
									<path d="M7 17L17 7M17 7H7M17 7V17"/>
								</svg>
							</div>
						</a>
					{/each}
				</div>
			</div>
		</div>
	</section>

	<!-- WRITING SECTION -->
	<section id="writing" class="writing">
		<div class="container">
			<div class="section-grid">
				<div class="section-label reveal">
					<span class="label-number">04</span>
					<span class="label-text">Writing</span>
				</div>

				<div class="writing-grid">
					{#each blogPosts as post, i}
						<a
							href={post.url}
							target="_blank"
							rel="noopener"
							class="blog-card reveal"
							style="--delay: {i * 0.1}s"
						>
							<span class="blog-number mono">{String(i + 1).padStart(2, '0')}</span>
							<span class="blog-title">{post.title}</span>
							<span class="blog-arrow">→</span>
						</a>
					{/each}
				</div>
			</div>
		</div>
	</section>

	<!-- FOOTER -->
	<footer class="footer">
		<div class="container">
			<div class="footer-content">
				<div class="footer-brand">
					<span class="mono">daniel@abeles:~$</span>
					<span class="footer-name gradient-text">Daniel Abeles</span>
				</div>
				<div class="footer-links">
					<a href="https://github.com/Den1al" target="_blank" rel="noopener">GitHub</a>
					<a href="https://twitter.com/Daniel_Abeles" target="_blank" rel="noopener">Twitter</a>
					<a href="https://www.linkedin.com/in/daniel-abeles" target="_blank" rel="noopener">LinkedIn</a>
					<a href="mailto:hello@abeles.dev">hello@abeles.dev</a>
				</div>
			</div>
			<div class="footer-bottom mono">
				<span>© {new Date().getFullYear()} All rights reserved</span>
			</div>
		</div>
	</footer>
</main>

<style>
	/* === SIDE NAVIGATION === */
	.side-nav {
		position: fixed;
		left: var(--space-8);
		top: 50%;
		transform: translateY(-50%);
		z-index: 100;
		display: flex;
		flex-direction: column;
		gap: var(--space-4);
		opacity: 0;
		transition: opacity 0.6s ease 0.5s;
	}

	.side-nav.mounted {
		opacity: 1;
	}

	.side-nav a {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 40px;
		height: 40px;
		border-radius: 50%;
		transition: all var(--transition-base);
	}

	.nav-dot {
		width: 8px;
		height: 8px;
		border-radius: 50%;
		background: var(--dark-500);
		transition: all var(--transition-base);
	}

	.side-nav a:hover .nav-dot,
	.side-nav a.active .nav-dot {
		background: var(--teal-200);
		box-shadow: 0 0 20px var(--teal-200);
	}

	.side-nav a.active .nav-dot {
		transform: scale(1.5);
	}

	/* === HERO === */
	.hero {
		min-height: 100vh;
		display: flex;
		align-items: center;
		justify-content: center;
		padding: var(--space-20) var(--space-8);
		position: relative;
	}

	.hero-content {
		text-align: center;
		max-width: 900px;
	}

	/* Terminal Window */
	.terminal-window {
		display: inline-block;
		background: var(--dark-800);
		border: 1px solid var(--dark-500);
		border-radius: var(--radius-lg);
		overflow: hidden;
		margin-bottom: var(--space-12);
		opacity: 0;
		transform: translateY(20px);
		transition: all 0.6s ease;
	}

	.terminal-window.mounted {
		opacity: 1;
		transform: translateY(0);
	}

	.terminal-header {
		display: flex;
		align-items: center;
		gap: var(--space-2);
		padding: var(--space-3) var(--space-4);
		background: var(--dark-700);
		border-bottom: 1px solid var(--dark-500);
	}

	.terminal-dot {
		width: 12px;
		height: 12px;
		border-radius: 50%;
	}

	.terminal-dot.red { background: #ff5f56; }
	.terminal-dot.yellow { background: #ffbd2e; }
	.terminal-dot.green { background: #27ca40; }

	.terminal-title {
		margin-left: auto;
		font-family: var(--font-display);
		font-size: var(--text-xs);
		color: var(--text-muted);
	}

	.terminal-body {
		padding: var(--space-6) var(--space-8);
		font-family: var(--font-display);
		font-size: var(--text-lg);
		color: var(--teal-200);
	}

	.terminal-prompt {
		color: var(--text-secondary);
	}

	.cursor {
		color: var(--teal-200);
		animation: blink 1s infinite;
	}

	/* Hero Title */
	.hero-title {
		font-size: var(--text-6xl);
		line-height: 1;
		margin-bottom: var(--space-8);
		opacity: 0;
		transform: translateY(30px);
		transition: all 0.8s ease 0.3s;
	}

	.hero-title.mounted {
		opacity: 1;
		transform: translateY(0);
	}

	.title-line {
		display: block;
	}

	.title-line:first-child {
		color: var(--text-muted);
		font-size: 0.5em;
		font-weight: 500;
		letter-spacing: 0.2em;
		text-transform: uppercase;
		margin-bottom: var(--space-2);
	}

	/* Hero Subtitle */
	.hero-subtitle {
		font-size: var(--text-xl);
		color: var(--text-secondary);
		max-width: 600px;
		margin: 0 auto var(--space-12);
		opacity: 0;
		transform: translateY(20px);
		transition: all 0.8s ease 0.5s;
	}

	.hero-subtitle.mounted {
		opacity: 1;
		transform: translateY(0);
	}

	.hero-subtitle a {
		color: var(--purple-200);
		font-weight: 600;
		position: relative;
	}

	.hero-subtitle a::after {
		content: '';
		position: absolute;
		bottom: -2px;
		left: 0;
		width: 100%;
		height: 2px;
		background: var(--purple-200);
		transform: scaleX(0);
		transition: transform var(--transition-base);
	}

	.hero-subtitle a:hover::after {
		transform: scaleX(1);
	}

	/* Hero Stats */
	.hero-stats {
		display: flex;
		justify-content: center;
		gap: var(--space-12);
		margin-bottom: var(--space-16);
		opacity: 0;
		transition: opacity 0.8s ease 0.7s;
	}

	.hero-stats.mounted {
		opacity: 1;
	}

	.stat-item {
		text-align: center;
		opacity: 0;
		transform: translateY(20px);
		animation: fadeInUp 0.6s ease forwards;
		animation-delay: calc(0.8s + var(--delay));
	}

	.stat-value {
		display: block;
		font-family: var(--font-display);
		font-size: var(--text-4xl);
		font-weight: 700;
		color: var(--teal-200);
		line-height: 1;
	}

	.stat-label {
		font-size: var(--text-sm);
		color: var(--text-muted);
		text-transform: uppercase;
		letter-spacing: 0.1em;
	}

	/* Scroll Indicator */
	.scroll-indicator {
		position: absolute;
		bottom: var(--space-12);
		left: 50%;
		transform: translateX(-50%);
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: var(--space-3);
		opacity: 0;
		transition: opacity 0.8s ease 1s;
	}

	.scroll-indicator.mounted {
		opacity: 1;
	}

	.scroll-text {
		font-size: var(--text-xs);
		color: var(--text-muted);
		text-transform: uppercase;
		letter-spacing: 0.2em;
	}

	.scroll-line {
		width: 1px;
		height: 60px;
		background: linear-gradient(to bottom, var(--purple-300), transparent);
		animation: float 2s ease-in-out infinite;
	}

	/* === SECTIONS COMMON === */
	section {
		padding: var(--space-32) 0;
	}

	.section-grid {
		display: grid;
		grid-template-columns: 200px 1fr;
		gap: var(--space-16);
	}

	.section-label {
		position: sticky;
		top: var(--space-32);
		height: fit-content;
	}

	.label-number {
		display: block;
		font-family: var(--font-display);
		font-size: var(--text-sm);
		color: var(--teal-200);
		margin-bottom: var(--space-2);
	}

	.label-text {
		font-family: var(--font-display);
		font-size: var(--text-2xl);
		font-weight: 700;
		color: var(--text-primary);
	}

	/* === ABOUT === */
	.quote {
		font-size: var(--text-2xl);
		font-weight: 300;
		color: var(--text-secondary);
		line-height: 1.5;
		margin-bottom: var(--space-8);
		position: relative;
		padding-left: var(--space-8);
		border: none;
		background: transparent;
	}

	.quote-mark {
		color: var(--purple-300);
		font-size: var(--text-4xl);
		font-family: Georgia, serif;
	}

	.about-text {
		font-size: var(--text-lg);
		line-height: 1.8;
		margin-bottom: var(--space-8);
	}

	.about-text strong {
		color: var(--teal-200);
	}

	.skills-cloud {
		display: flex;
		flex-wrap: wrap;
		gap: var(--space-3);
	}

	.skill-tag {
		font-family: var(--font-display);
		font-size: var(--text-sm);
		padding: var(--space-2) var(--space-4);
		background: var(--dark-600);
		border: 1px solid var(--dark-500);
		border-radius: var(--radius-sm);
		color: var(--text-secondary);
		transition: all var(--transition-base);
	}

	.skill-tag:hover {
		border-color: var(--purple-300);
		color: var(--purple-200);
	}

	/* === BENTO GRID === */
	.bento-grid {
		display: grid;
		grid-template-columns: 2fr 1fr;
		grid-template-rows: auto auto;
		gap: var(--space-6);
	}

	.bento-card {
		background: var(--dark-800);
		border: 1px solid var(--dark-500);
		border-radius: var(--radius-xl);
		padding: var(--space-8);
		transition: all var(--transition-base);
	}

	.bento-card:hover {
		border-color: var(--purple-400);
		transform: translateY(-4px);
		box-shadow: var(--shadow-glow);
	}

	.bento-large {
		grid-row: span 2;
	}

	.bento-accent {
		background: linear-gradient(135deg, var(--purple-500) 0%, var(--purple-600) 100%);
		border: none;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.bento-accent:hover {
		transform: translateY(-4px) scale(1.02);
		box-shadow: var(--shadow-glow);
	}

	.accent-card-content {
		text-align: center;
	}

	.accent-number {
		display: block;
		font-family: var(--font-display);
		font-size: var(--text-5xl);
		font-weight: 700;
		color: var(--teal-200);
		line-height: 1;
	}

	.accent-label {
		font-size: var(--text-sm);
		color: var(--text-secondary);
		text-transform: uppercase;
		letter-spacing: 0.1em;
	}

	.card-title {
		font-size: var(--text-lg);
		color: var(--text-muted);
		margin-bottom: var(--space-6);
		font-weight: 500;
	}

	/* Timeline */
	.timeline {
		position: relative;
		padding-left: var(--space-8);
	}

	.timeline::before {
		content: '';
		position: absolute;
		left: 4px;
		top: 8px;
		bottom: 8px;
		width: 1px;
		background: linear-gradient(to bottom, var(--purple-300), var(--dark-500));
	}

	.timeline-item {
		position: relative;
		padding-bottom: var(--space-6);
	}

	.timeline-item:last-child {
		padding-bottom: 0;
	}

	.timeline-marker {
		position: absolute;
		left: calc(-1 * var(--space-8) + 1px);
		top: 6px;
		width: 8px;
		height: 8px;
		background: var(--dark-500);
		border-radius: 50%;
		transition: all var(--transition-base);
	}

	.timeline-marker.current {
		background: var(--teal-200);
		box-shadow: 0 0 20px var(--teal-200);
	}

	.pulse-ring {
		position: absolute;
		inset: -4px;
		border: 1px solid var(--teal-200);
		border-radius: 50%;
		animation: pulse 2s ease-in-out infinite;
	}

	.timeline-header {
		display: flex;
		justify-content: space-between;
		align-items: baseline;
		margin-bottom: var(--space-1);
	}

	.company-name {
		font-weight: 600;
		color: var(--text-primary);
	}

	.company-name:hover {
		color: var(--teal-200);
	}

	.timeline-years {
		font-size: var(--text-sm);
		color: var(--text-muted);
	}

	.timeline-position {
		font-size: var(--text-sm);
		color: var(--text-secondary);
		margin: 0;
	}

	/* Conference List */
	.conference-list {
		display: flex;
		flex-direction: column;
		gap: var(--space-3);
	}

	.conference-item {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: var(--space-3) var(--space-4);
		background: var(--dark-700);
		border-radius: var(--radius-md);
		transition: all var(--transition-base);
	}

	.conference-item:hover {
		background: var(--dark-600);
		transform: translateX(4px);
	}

	.conf-name {
		font-weight: 500;
		color: var(--text-secondary);
	}

	.conference-item:hover .conf-name {
		color: var(--text-primary);
	}

	.conf-year {
		font-size: var(--text-sm);
		color: var(--purple-200);
	}

	/* === PROJECTS === */
	.projects-showcase {
		display: flex;
		flex-direction: column;
		gap: var(--space-6);
	}

	.project-card {
		display: grid;
		grid-template-columns: 80px 1fr auto;
		gap: var(--space-6);
		align-items: center;
		padding: var(--space-8);
		background: var(--dark-800);
		border: 1px solid var(--dark-500);
		border-radius: var(--radius-xl);
		transition: all var(--transition-slow);
		text-decoration: none;
	}

	.project-card:hover {
		border-color: var(--teal-300);
		transform: translateX(8px);
		box-shadow: var(--shadow-glow-teal);
	}

	.project-icon {
		font-size: var(--text-4xl);
		width: 80px;
		height: 80px;
		display: flex;
		align-items: center;
		justify-content: center;
		background: var(--dark-700);
		border-radius: var(--radius-lg);
	}

	.project-name {
		font-size: var(--text-xl);
		color: var(--text-primary);
		margin-bottom: var(--space-1);
	}

	.project-tagline {
		font-family: var(--font-display);
		font-size: var(--text-sm);
		color: var(--teal-200);
		margin-bottom: var(--space-2);
	}

	.project-desc {
		font-size: var(--text-sm);
		color: var(--text-muted);
		margin: 0;
		max-width: 500px;
	}

	.project-arrow {
		color: var(--text-muted);
		transition: all var(--transition-base);
	}

	.project-card:hover .project-arrow {
		color: var(--teal-200);
		transform: translate(4px, -4px);
	}

	/* === WRITING === */
	.writing-grid {
		display: flex;
		flex-direction: column;
		gap: var(--space-3);
	}

	.blog-card {
		display: grid;
		grid-template-columns: 50px 1fr auto;
		gap: var(--space-4);
		align-items: center;
		padding: var(--space-5) var(--space-6);
		background: transparent;
		border: 1px solid var(--dark-500);
		border-radius: var(--radius-md);
		transition: all var(--transition-base);
	}

	.blog-card:hover {
		background: var(--dark-800);
		border-color: var(--purple-400);
		transform: translateX(8px);
	}

	.blog-number {
		font-size: var(--text-sm);
		color: var(--purple-300);
	}

	.blog-title {
		font-weight: 500;
		color: var(--text-secondary);
		transition: color var(--transition-fast);
	}

	.blog-card:hover .blog-title {
		color: var(--text-primary);
	}

	.blog-arrow {
		color: var(--text-muted);
		transition: all var(--transition-base);
	}

	.blog-card:hover .blog-arrow {
		color: var(--teal-200);
		transform: translateX(4px);
	}

	/* === FOOTER === */
	.footer {
		padding: var(--space-16) 0 var(--space-8);
		border-top: 1px solid var(--dark-600);
	}

	.footer-content {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-bottom: var(--space-8);
	}

	.footer-brand {
		display: flex;
		flex-direction: column;
		gap: var(--space-2);
	}

	.footer-brand .mono {
		font-size: var(--text-sm);
		color: var(--text-muted);
	}

	.footer-name {
		font-family: var(--font-display);
		font-size: var(--text-2xl);
		font-weight: 700;
	}

	.footer-links {
		display: flex;
		gap: var(--space-8);
	}

	.footer-links a {
		font-size: var(--text-sm);
		color: var(--text-muted);
		transition: color var(--transition-fast);
	}

	.footer-links a:hover {
		color: var(--teal-200);
	}

	.footer-bottom {
		text-align: center;
		font-size: var(--text-sm);
		color: var(--text-muted);
	}

	/* === RESPONSIVE === */
	@media (max-width: 1024px) {
		.side-nav {
			display: none;
		}

		.section-grid {
			grid-template-columns: 1fr;
			gap: var(--space-8);
		}

		.section-label {
			position: static;
			display: flex;
			align-items: baseline;
			gap: var(--space-4);
		}

		.bento-grid {
			grid-template-columns: 1fr;
		}

		.bento-large {
			grid-row: auto;
		}

		.project-card {
			grid-template-columns: 60px 1fr;
		}

		.project-arrow {
			display: none;
		}
	}

	@media (max-width: 768px) {
		.hero {
			padding: var(--space-16) var(--space-4);
		}

		.terminal-body {
			font-size: var(--text-base);
			padding: var(--space-4) var(--space-6);
		}

		.project-card {
			grid-template-columns: 1fr;
			text-align: center;
		}

		.project-icon {
			margin: 0 auto;
		}

		.project-info {
			display: flex;
			flex-direction: column;
			align-items: center;
		}

		.project-tagline {
			text-align: center;
		}

		.project-desc {
			max-width: 100%;
			text-align: center;
		}

		.footer-content {
			flex-direction: column;
			gap: var(--space-8);
			text-align: center;
		}

		.footer-links {
			flex-wrap: wrap;
			justify-content: center;
			gap: var(--space-4);
		}
	}
</style>
