<script>
  let state = {
    work: true,
    priv: true,
    sleep: false
  }

  function random(one, two) {
    return Math.random() < 0.5 ? one : two
  }

  function toggle(e) {
    const name = e.target.name
    let choise
    if (state.work && state.priv && state.sleep) {
      if (name === 'work') {
        choise = random('priv', 'sleep')
      } else if (name === 'priv') {
        choise = random('work', 'sleep')
      } else if (name === 'sleep') {
        choise = random('work', 'priv')
      }
      state[choise] = false
    }
  }

</script>

<main>
  <fieldset>
    <label>
      <input name="work" type="checkbox" role="switch" bind:checked={state['work']} on:change={toggle} />
      Работа
    </label>
    <label>
      <input name="priv" type="checkbox" role="switch" bind:checked={state['priv']} on:change={toggle} />
      Личная жизнь
    </label>
    <label>
      <input name="sleep" type="checkbox" role="switch" bind:checked={state['sleep']} on:change={toggle} />
      Сон
    </label>
  </fieldset>
</main>

<style>
  fieldset {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }
</style>
