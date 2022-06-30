<script>
  import logo from './assets/svelte.png'
  import Counter from './lib/Counter.svelte'
  // import { registerSW } from "virtual:pwa-register";
  console.log('h')
// if ("serviceWorker" in navigator) {
//   console.log('hi')
//   // && !/localhost/.test(window.location)) {
//   registerSW();
//   console.log('hi2')
// }
if ('serviceWorker' in navigator) {
    window.addEventListener('load', () => {
      navigator.serviceWorker.register('/sw.js')
        .then(registration => {
          console.log(`Service Worker registered! Scope: ${registration.scope}`);
        })
        .catch(err => {
          console.log(`Service Worker registration failed: ${err}`);
        });
    });
  }
</script>

<main>
  <img src={logo} alt="Svelte Logo" />
  <h1>Hello world!</h1>

  <Counter />

  <p>
    Visit <a href="https://svelte.dev">svelte.dev</a> to learn how to build Svelte
    apps.
  </p>

  <p>
    Check out <a href="https://github.com/sveltejs/kit#readme">SvelteKit</a> for
    the officially supported framework, also powered by Vite!
  </p>
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

  img {
    height: 16rem;
    width: 16rem;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4rem;
    font-weight: 100;
    line-height: 1.1;
    margin: 2rem auto;
    max-width: 14rem;
  }

  p {
    max-width: 14rem;
    margin: 1rem auto;
    line-height: 1.35;
  }

  @media (min-width: 480px) {
    h1 {
      max-width: none;
    }

    p {
      max-width: none;
    }
  }
</style>
