<script>
  import '../app.css'
</script>

<main>
  <slot />
</main>

<footer>
  <p>Copyright 2022</p>
</footer>

<style>
  main {
    flex: 1;
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 100%;
  }

  footer {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 40px;
  }

  @media (min-width: 480px) {
    footer {
      padding: 40px 0;
    }
  }
</style>
