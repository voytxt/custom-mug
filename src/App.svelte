<script>
  let mugLink = '';

  let text = 'Never gonna give you up';
  let backgroundColor = '#36393f';

  $: {
    let startingText = text;
    let startingBackgroundColor = backgroundColor;
    setTimeout(() => {
      if (startingText === text && startingBackgroundColor === backgroundColor) mugLink = getMugSrc();
    }, 500);
  }

  function getMugSrc() {
    return `https://urbandictionary.store/render/preview/mug/back.jpg?logo-variant=dark&word&bg=000000&fg=000000&fill=${backgroundColor
      .slice(1)
      .toUpperCase()}&meaning=${text}`;
  }
</script>

<!-- svelte-ignore a11y-autofocus -->
<input type="text" autofocus bind:value={text} />
<div class="form">
  <label>
    <span>Background color</span>
    <button on:click={() => (backgroundColor = '#36393f')}>Discord gray</button>
    <input type="color" bind:value={backgroundColor} />
  </label>
</div>
<img src={mugLink} alt="Mug with custom text" />
<footer>
  <small>
    &copy; {new Date().getFullYear()} Vojta | <a href="https://github.com/vojta-dev/custom-mug">GitHub</a> | Mug from
    <a href="https://urbandictionary.store/">UrbanDictionary Store</a> | Colors from
    <a href="https://tailwindcss.com/docs/customizing-colors#color-palette-reference">Tailwind</a>
  </small>
</footer>

<style>
  :global(body) {
    margin: 0;
    background-color: black;
    color: white;
    height: 100vh;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  :global(#app) {
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  input,
  button {
    font-family: inherit;
  }
  input[type='text'] {
    margin-top: 3rem;
    width: 50rem;
    height: 5rem;
    padding: 1rem 1.5rem;
    font-size: 3rem;
    background-color: black;
    color: white;
    border: 4px solid #10b981;
    border-radius: 2rem;
    font-family: inherit;
  }

  .form {
    margin-top: 2rem;
  }
  .form label {
    display: flex;
    gap: 0.5rem;
  }
  .form label span {
    align-self: center;
  }

  img {
    margin-top: 2rem;
    max-width: 60vh;
  }

  footer {
    position: absolute;
    text-align: center;
    bottom: 1rem;
    width: 100%;
  }

  footer a {
    color: #60a5fa;
    text-decoration: none;
  }
</style>
