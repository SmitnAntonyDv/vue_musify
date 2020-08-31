<template>
  <div id="app">
    <header>
      <h1>General Music title</h1>
    </header>
    <main>
      <section class="player">
        <h2 class="song-title">
          {{currentSong.title}} -
          <span>{{currentSong.artist}}</span>
          <div class="controls">
            <button class="prev">prev</button>
            <button class="play" v-if="!isActive" v-on:click="play">play</button>
            <button class="play" v-else v-on:click="pause">pauze</button>
            <button class="next">next</button>
          </div>
        </h2>
      </section>
    </main>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      currentSong: {},
      index: 0,
      isActive: false,
      songs: [
        {
          title: "Energy",
          artist: "Ben-Sound.com",
          type: "royalty-free",
          src: require(`./assets/Energy.mp3`),
        },
        {
          title: "Inspire",
          artist: "Ben-Sound.com",
          type: "royalty-free",
          src: require(`./assets/Inspire.mp3`),
        },
        {
          title: "Newdawn",
          artist: "Ben-Sound.com",
          type: "royalty-free",
          src: require(`./assets/Newdawn.mp3`),
        },
      ],
      // Html5 new audio file function that allows for playing audio in browser
      player: new Audio(),
    };
  },
  created() {
    this.currentSong = this.songs[this.index];
    this.player.src = this.currentSong.src;
    // this.player.play();
  },
  methods: {
    play(song) {
      if (typeof song.src != "undefined") {
        this.currentSong = song;
        this.player.src = this.currentSong.src;
      }
      this.player.play();
      this.isActive = true;
    },
    pause() {
      this.player.pause();
      this.isActive = false;
    },
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
