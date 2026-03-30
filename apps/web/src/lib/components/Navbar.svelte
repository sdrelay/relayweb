<script lang="ts">
  // No props needed
</script>

<nav class="navbar">
  <div class="logo">
    <i class="fas fa-gamepad"></i>          <!-- gaming icon -->
    <span>Relay</span>
    <span style="color: #ff8c42">Gaming</span>
  </div>
  <div class="nav-links">
    <a href="#features">Features</a>
    <a href="#about">About</a>
    <a
      href="#github"
      // target="_blank"
      class="btn-outline"
    >
      <i class="fab fa-github"></i> GitHub
    </a>
  </div>
</nav>

<style>
  /* same as before, just adjust the logo icon if needed */
  .navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
    flex-wrap: wrap;
    gap: 1rem;
    background: rgba(3, 7, 18, 0.8);
    backdrop-filter: blur(12px);
    border-radius: 2rem;
    margin: 1rem 0;
    border: 1px solid rgba(255, 140, 66, 0.2);
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
  }

  .logo {
    display: flex;
    align-items: center;
    gap: 0.6rem;
    font-weight: 700;
    font-size: 1.5rem;
    letter-spacing: -0.02em;
  }

  .logo i {
    font-size: 1.8rem;
    color: #ff3e00;
  }

  .logo span:first-of-type {
    background: linear-gradient(135deg, #ff3e00, #ff8c42);
    background-clip: text;
    -webkit-background-clip: text;
    color: transparent;
  }

  .nav-links {
    display: flex;
    gap: 2rem;
    align-items: center;
    flex-wrap: wrap;
  }

  .nav-links a {
    text-decoration: none;
    color: #cbd5e1;
    font-weight: 500;
    transition: 0.2s;
  }

  .nav-links a:hover {
    color: #ff8c42;
  }

  .btn-outline {
    border: 1.5px solid rgba(255, 62, 0, 0.6);
    background: transparent;
    padding: 0.5rem 1.2rem;
    border-radius: 40px;
    font-weight: 600;
    transition: 0.25s;
    color: white;
  }

  .btn-outline:hover {
    background: rgba(255, 62, 0, 0.15);
    border-color: #ff3e00;
    transform: scale(0.98);
  }

  @media (max-width: 760px) {
    .navbar {
      flex-direction: column;
      text-align: center;
      padding: 1rem;
    }
  }
</style>
