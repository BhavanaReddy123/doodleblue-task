<template>
  <div id="app">
    <header>
      <div class="logo-outer">
        <img src="../../docs/doodle.gif" alt="logo">
        <p>doodleblue</p>
      </div>
    </header>
    <main>
      <section class="title">
        <h1>WE DISCOVER, DESIGN & BUILD STRATEGY TO HELP BRANDS</h1>
        <p class="subtitle">Digital Strategy Consulting & Design. Innovate. Transform</p>
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
  .logo-outer {
    width: 100px;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    p {
      font-size: 24px;
      font-weight: 600;
      color: #000;
      margin-left: 1rem;
    }
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
      color: #000;
      font-weight: 600;
      font-size: 2rem;
      line-height: 1.5rem;
      margin-bottom: 1rem;
    }
    .subtitle {
      color: #8f8d8d;
      font-size: 1.2rem;
    }
  }

</style>
