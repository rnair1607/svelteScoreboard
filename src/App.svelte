<script>
  import Navbar from "./Navbar.svelte";
  import Player from "./Player.svelte";
  import AddPlayer from "./AddPlayer.svelte";

  let players = [
    { name: "Rohan", points: 83 },
    { name: "Robert", points: 93 },
    { name: "Ronak", points: 98 },
  ];

  const addPlayer = (e) => {
    const newPlayer = e.detail;
    players = [...players, newPlayer];
  };

  const removePlayer = (e) => {
    players = players.filter((p) => p.name !== e.detail);
  };
</script>

<style>

</style>

<Navbar />
<div class="container">
  <AddPlayer on:addplayer={addPlayer} />

  {#if players.length === 0}
    <p>No Players!</p>
  {:else}
    {#each players as player}
      <Player
        name={player.name}
        points={player.points}
        on:removeplayer={removePlayer} />
    {/each}
  {/if}
</div>
