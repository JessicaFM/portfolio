<script>
  let backgroundPrimary, colorPrimaryLight
</script>

<header style="--background-color: {backgroundPrimary}; --primary-color: {colorPrimaryLight}">
  <a href="/" rel="home" class="home-link">Jessica F</a>
  <navbar class="navbar offset-right">
    <a href="#about" class="navbar-link">About</a>
    <a href="#experience" class="navbar-link">Experience</a>
    <a href="#contact" class="navbar-link">Contact</a>
  </navbar>
</header>

<style lang="scss">
  header {
    display: flex;
    justify-content: space-between;
    background: var(--background-color);
    margin: 0;
    padding: 0.5rem calc(5vw - 0.5rem);
    a {
      color: white;
      text-decoration: none;
      font-size: 1.2rem;
    }
    .home-link {
      font-weight: 600;   
      font-size: 1.4rem; 
    }
    .navbar {
      gap: 1rem;
      display: flex;
      justify-content: flex-start;
      a {
        padding: .5rem;;
      }
    }
}
</style>