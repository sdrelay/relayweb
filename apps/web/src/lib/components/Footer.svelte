<footer class="footer">
  <div>
    <i class="fas fa-heart" style="color: #ff3e00"></i> Turborepo + Svelte • Open source
  </div>
  <div>
    <a href="https://turbo.build" target="_blank"><i class="fas fa-globe"></i> Turbo.build</a>
    &nbsp;|&nbsp;
    <a href="https://svelte.dev" target="_blank"><i class="fab fa-svelte"></i> Svelte</a>
    &nbsp;|&nbsp;
    <a href="#top"><i class="fas fa-arrow-up"></i> Back to top</a>
  </div>
</footer>

<style>
  .footer {
    margin-top: 5rem;
    border-top: 1px solid rgba(255, 255, 255, 0.05);
    padding: 2rem 0;
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 1rem;
    font-size: 0.85rem;
    color: #7e8aa2;
  }

  .footer a {
    color: #ffaa6e;
    text-decoration: none;
  }

  @media (max-width: 760px) {
    .footer {
      flex-direction: column;
      text-align: center;
    }
  }
</style>
