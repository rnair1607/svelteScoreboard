<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  let player = {
    name: "",
    points: 1,
  };

  const onSubmit = (e) => {
    e.preventDefault();
    if (player.name.length !== 0 && player.points > 0) {
      dispatch("addplayer", player);
    } else {
      alert("Enter data to add!");
    }
    player = {
      name: "",
      points: 0,
    };
  };
</script>

<div class="card">
  <form on:submit={onSubmit} class="grid-3">
    <input type="text" placeholder="Player Name" bind:value={player.name} />
    <input type="number" placeholder="Points" bind:value={player.points} />
    <input type="submit" class="btn btn-primary" value="Add Player" />
  </form>
</div>
