<script lang="ts">
  import { onMount } from 'svelte';
  import { fly } from 'svelte/transition';
  import Navbar from '$lib/components/Navbar.svelte';
  import Footer from '$lib/components/Footer.svelte';

  let currentSection = $state<'home' | 'about'>('home');

  function handleHashChange() {
    const hash = window.location.hash.slice(1);
    if (hash === 'about') {
      currentSection = 'about';
    } else {
      currentSection = 'home';
    }
  }

  onMount(() => {
    handleHashChange();
    window.addEventListener('hashchange', handleHashChange);
    return () => window.removeEventListener('hashchange', handleHashChange);
  });
</script>

<svelte:head>
  <title>Relay Gaming | Home</title>
  <link
    href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,500;14..32,600;14..32,700;14..32,800&display=swap"
    rel="stylesheet"
  />
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css"
  />
</svelte:head>

<div class="container">
  <Navbar />

  <!-- Home section (Hero + Features) -->
  {#if currentSection === 'home'}
    <div transition:fly={{ duration: 300, y: 20, opacity: 0 }}>
      <section class="hero">
        <div class="hero-badge">
          <i class="fas fa-cubes"></i> Monorepo · Turbocharged · Gaming Ready
        </div>
        <h1>Relay Gaming<br />The Svelte + Turborepo Stack</h1>
        <p>
          Build the ultimate gaming platform — from leaderboards to real‑time
          multiplayer — with a scalable monorepo powered by SvelteKit, Turborepo,
          and TypeScript.
        </p>
        <div class="hero-buttons">
          <a href="#install" class="btn-primary"
            ><i class="fas fa-terminal"></i> Start building</a
          >
          <a href="https://turbo.build/repo" target="_blank" class="btn-secondary"
            ><i class="fas fa-book-open"></i> Turborepo docs</a
          >
        </div>
      </section>

      <section id="features">
        <h2 class="section-title">Why Relay Gaming?</h2>
        <div class="features-grid">
          <div class="feature-card">
            <div class="feature-icon"><i class="fas fa-layer-group"></i></div>
            <h3>Monorepo for Games</h3>
            <p>
              Manage multiple game clients, admin dashboards, shared UI, and game
              logic in one repo. Turborepo caches builds and runs tasks in parallel.
            </p>
          </div>
          <div class="feature-card">
            <div class="feature-icon"><i class="fab fa-svelte"></i></div>
            <h3>Svelte & SvelteKit</h3>
            <p>
              Reactive, lightning‑fast UI for game stats, leaderboards, and
              real‑time updates. Svelte 5 with runes gives you fine‑grained control.
            </p>
          </div>
          <div class="feature-card">
            <div class="feature-icon"><i class="fas fa-rocket"></i></div>
            <h3>Turbocharged DX</h3>
            <p>
              Incremental builds, remote caching, and optimized task orchestration.
              Hot module replacement across the whole monorepo.
            </p>
          </div>
          <div class="feature-card">
            <div class="feature-icon"><i class="fas fa-code-branch"></i></div>
            <h3>Shared Packages</h3>
            <p>
              Reusable UI components, configs, and game utilities across apps.
              Import instantly with workspace aliases.
            </p>
          </div>
        </div>
      </section>
    </div>
  {:else}
    <!-- About section -->
    <div transition:fly={{ duration: 300, y: 20, opacity: 0 }}>
      <section id="about" class="about-section">
        <h2 class="section-title">About Relay Gaming</h2>
        <div class="about-content">
          <p>
            Relay Gaming is a modern monorepo starter built for game developers who want to ship
            fast and scale effortlessly. We combine the power of <strong>SvelteKit</strong> and
            <strong>Turborepo</strong> to give you a rock‑solid foundation for your next gaming platform.
          </p>
          <p>
            Our mission is to empower creators with a toolset that eliminates boilerplate, speeds up
            iteration, and keeps your codebase organized across multiple projects.
          </p>
          <p>
            Whether you're building a leaderboard, a real‑time multiplayer dashboard, or a full‑fledged
            game portal, Relay Gaming gives you the building blocks you need.
          </p>
          <div class="team">
            <h3>Built with ❤️ by</h3>
            <div class="team-member">
              <i class="fas fa-user-astronaut"></i> Sadri (sdrelay)
            </div>
            <div class="team-member">
              <i class="fas fa-code-branch"></i> Open source contributors
            </div>
          </div>
          <div class="cta">
            <a href="https://github.com/sdrelay/relayweb" target="_blank" class="btn-primary">
              <i class="fab fa-github"></i> Star on GitHub
            </a>
          </div>
        </div>
      </section>
    </div>
  {/if}

  <Footer />
</div>

<style>
  :global(body) {
    font-family: 'Inter', sans-serif;
    background: radial-gradient(circle at 10% 20%, #0b1120, #03050b);
    color: #eff3f8;
    line-height: 1.5;
  }

  .container {
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 1.5rem;
  }

  /* Hero section */
  .hero {
    padding: 4rem 0 5rem;
    text-align: center;
  }

  .hero-badge {
    background: rgba(255, 62, 0, 0.12);
    padding: 0.3rem 1rem;
    border-radius: 40px;
    display: inline-block;
    font-size: 0.85rem;
    font-weight: 500;
    backdrop-filter: blur(2px);
    margin-bottom: 1.5rem;
    border: 0.5px solid rgba(255, 98, 0, 0.4);
  }

  .hero h1 {
    font-size: 3.3rem;
    font-weight: 800;
    letter-spacing: -0.02em;
    line-height: 1.2;
    background: linear-gradient(to right, #ffffff, #ffb085);
    background-clip: text;
    -webkit-background-clip: text;
    color: transparent;
    margin-bottom: 1rem;
  }

  .hero p {
    font-size: 1.2rem;
    color: #a0aec0;
    max-width: 680px;
    margin: 0 auto 2rem;
  }

  .hero-buttons {
    display: flex;
    gap: 1rem;
    justify-content: center;
    flex-wrap: wrap;
  }

  .btn-primary {
    background: linear-gradient(105deg, #ff3e00, #ff6a2c);
    border: none;
    padding: 0.8rem 1.8rem;
    border-radius: 40px;
    font-weight: 600;
    color: white;
    font-size: 1rem;
    cursor: pointer;
    transition: 0.25s;
    box-shadow: 0 8px 18px rgba(255, 62, 0, 0.25);
    display: inline-flex;
    align-items: center;
    gap: 0.6rem;
  }

  .btn-primary:hover {
    transform: translateY(-3px);
    box-shadow: 0 15px 25px -8px rgba(255, 62, 0, 0.4);
    background: linear-gradient(105deg, #ff571f, #ff7a3c);
  }

  .btn-secondary {
    background: rgba(255, 255, 255, 0.05);
    backdrop-filter: blur(4px);
    border: 1px solid rgba(255, 255, 255, 0.15);
    padding: 0.8rem 1.8rem;
    border-radius: 40px;
    font-weight: 500;
    transition: 0.2s;
    color: #eff3f8;
  }

  .btn-secondary:hover {
    background: rgba(255, 62, 0, 0.2);
    border-color: #ff3e00;
  }

  .section-title {
    font-size: 2rem;
    font-weight: 700;
    text-align: center;
    margin-bottom: 3rem;
    background: linear-gradient(135deg, #f0f4ff, #ffb07c);
    background-clip: text;
    -webkit-background-clip: text;
    color: transparent;
  }

  .features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 2rem;
    margin: 3rem 0;
  }

  .feature-card {
    background: rgba(15, 25, 45, 0.5);
    backdrop-filter: blur(8px);
    border: 1px solid rgba(255, 140, 66, 0.2);
    border-radius: 2rem;
    padding: 1.8rem;
    transition: all 0.3s ease;
  }

  .feature-card:hover {
    border-color: #ff6a2c;
    transform: translateY(-6px);
    background: rgba(20, 30, 55, 0.7);
    box-shadow: 0 20px 30px -12px rgba(0, 0, 0, 0.4);
  }

  .feature-icon {
    font-size: 2.3rem;
    color: #ff6a2c;
    margin-bottom: 1rem;
  }

  .feature-card h3 {
    font-size: 1.4rem;
    font-weight: 600;
    margin-bottom: 0.8rem;
  }

  .feature-card p {
    color: #b9c7d9;
    font-size: 0.95rem;
  }

  /* About section styles */
  .about-section {
    padding: 4rem 0 5rem;
    max-width: 800px;
    margin: 0 auto;
    text-align: center;
  }

  .about-content {
    background: rgba(15, 25, 45, 0.5);
    backdrop-filter: blur(8px);
    border: 1px solid rgba(255, 140, 66, 0.2);
    border-radius: 2rem;
    padding: 2rem;
    text-align: left;
  }

  .about-content p {
    margin-bottom: 1.2rem;
    font-size: 1.1rem;
    line-height: 1.6;
  }

  .team {
    margin: 2rem 0;
    text-align: center;
  }

  .team h3 {
    font-size: 1.3rem;
    margin-bottom: 1rem;
    color: #ffaa6e;
  }

  .team-member {
    margin: 0.5rem 0;
    font-size: 1rem;
    display: inline-block;
    margin-right: 1.5rem;
  }

  .team-member i {
    margin-right: 0.5rem;
    color: #ff8c42;
  }

  .cta {
    text-align: center;
    margin-top: 2rem;
  }

  @media (max-width: 760px) {
    .hero h1 {
      font-size: 2.3rem;
    }
    .about-content {
      padding: 1.5rem;
    }
  }
</style>
