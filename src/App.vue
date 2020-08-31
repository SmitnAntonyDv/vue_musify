<template>
  <div id="app">
    <header>
      <h1>General Music title</h1>
    </header>
    <main>
      <section class="player">
        <h2 class="song-title">{{currentSong.title}}</h2>
      </section>
    </main>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      currentSong: {
        title: "TESTING TITLE",
      },
      songs: [
        {
          title: "Energy",
          provider: "Ben-Sound.com",
          type: "royalty-free",
          src: require(`./assets/Energy.mp3`),
        },
        {
          title: "Inspire",
          provider: "Ben-Sound.com",
          type: "royalty-free",
          src: require(`./assets/Inspire.mp3`),
        },
        {
          title: "Newdawn",
          provider: "Ben-Sound.com",
          type: "royalty-free",
          src: require(`./assets/Newdawn.mp3`),
        },
      ],
    };
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  font-family: sans-serif;
}
header {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
  background: #212122;
  color: #ffffff;
}
</style>
