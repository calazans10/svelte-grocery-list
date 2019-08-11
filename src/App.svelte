<script>
  let items = [
    { id: 1, name: "Milk", done: false },
    { id: 2, name: "Bread", done: true },
    { id: 3, name: "Eggs", done: false }
  ];

  let name = "";

  const addItem = () => {
    items = [...items, { id: Math.random(), name, done: false }];
    name = "";
  };

  const remove = item => (items = items.filter(i => i !== item));
</script>

<style type="text/scss">
  $base-font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;

  div,
  h1 {
    color: #333;
    max-width: 300px;
    font-family: $base-font-family;
  }

  #name {
    width: 100%;
  }

  form {
    margin-bottom: 0.5em;
  }

  input[type="text"] {
    outline: none;
    margin: 0;

    &:focus {
      border-color: #dc4f21;
      box-shadow: 0 0 2px #dc4f21;
    }
  }

  input[type="checkbox"] {
    margin: 0 10px 0 0;
  }

  li button {
    float: right;
    border: none;
    background: transparent;
    padding: 0;
    margin: 0;
    color: #dc4f21;
    font-size: 18px;
    cursor: pointer;

    &:hover {
      transform: scale(2);
    }

    &:focus {
      outline: #dc4f21;
    }
  }

  label {
    display: block;
    text-transform: uppercase;
    font-size: 0.8em;
    color: #777;
  }

  li {
    list-style: none;
    padding: 6px 10px;
    border-bottom: 1px solid #ddd;

    &:last-child {
      border-bottom: none;
    }
  }

  ul {
    padding-left: 0;
  }

  .done span {
    opacity: 0.4;
  }
</style>

<div>
  <h1>Grocery List 🗒️</h1>

  <form on:submit|preventDefault={addItem}>
    <label for="name">Add an item</label>
    <input id="name" type="text" bind:value={name} />
  </form>

  <ul>
    {#each items as item}
      <li class:done={item.done}>
        <input type="checkbox" bind:checked={item.done} />
        <span>{item.name}</span>
        <button on:click={() => remove(item)}>❌</button>
      </li>
    {/each}
  </ul>
</div>
