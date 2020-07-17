<template>
  <div id="app">
    <header>
      <div class="logo-outer">
        <img src="../../docs/zoomrx.png" alt="logo">
      </div>
    </header>
    <main>
      <section class="title">
        <h1>About Zoomrx</h1>
        <p class="subtitle">Strategic healthcare consulting.</p>
      </section>
      <section>
        <board/>
      </section>
    </main>
  </div>
</template>


<script>
import Board from 'elements/Board'
export default {
  components: {
    Board
  }
}
</script>

<style lang="scss">
  html, body {
    height: 100%;
  }

  body {
    padding: 20px;
  }
  header {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    background-color: #FFFFFF;
    box-shadow: 1px 4px 8px rgba(0, 0, 0, 0.5);
    display: block;
    z-index: 1;
    .logo-outer {
      padding: 1rem;
    }
  }
  section {
    &.title {
      margin-top: 7rem;
    }
    h1 {
      color: #113661;
      font-weight: 600;
      font-size: 2rem;
      line-height: 1.5rem;
      margin-bottom: 1rem;
    }
    .subtitle {
      color: #3b3b3b;
      font-size: 1.2rem;
    }
  }

</style>
