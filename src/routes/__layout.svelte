<script>
  import Footer from '$lib/Footer.svelte'
  import Navbar from '$lib/Navbar.svelte'
  import '../app.css'
</script>

<div class="box">
  <header>
    <Navbar text="Json Parser" />
  </header>

  <main>
    <slot />
  </main>

  <Footer />
</div>

<style>
  .box {
    display: flex;
    flex-flow: column;
    height: 100vh;
  }
  main {
    flex: 1;
    display: flex;
    flex-direction: column;
    width: 100%;
  }
</style>
