<template>
  <div id="app">
    <header>
      <h1>General Music title</h1>
    </header>
    <main>
      <section class="player">
        <h2 class="song-title">
          {{ currentSong.title }} -
          <span>{{ currentSong.artist }}</span>
          <div class="controls">
            <button class="prev" v-on:click="prev">prev</button>
            <button class="play" v-if="!isActive" v-on:click="play">
              play
            </button>
            <button class="play" v-else v-on:click="pause">pauze</button>
            <button class="next" v-on:click="next">next</button>
          </div>
        </h2>
      </section>
      <section class="playlist">
        <button v-for="song in songs" :key="song.id" v-on:click="play(song)">
          {{ song.title }} - {{ song.artist }}
        </button>
      </section>
    </main>
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';
export default {
  name: 'App',
  data() {
    return {
      currentSong: {},
      index: 0,
      isActive: false,
      songs: [
        {
          id: uuidv4(),
          title: 'Energy',
          artist: 'Ben-Sound.com',
          type: 'royalty-free',
          src: require(`./assets/Energy.mp3`),
        },
        {
          id: uuidv4(),
          title: 'Inspire',
          artist: 'Ben-Sound.com',
          type: 'royalty-free',
          src: require(`./assets/Inspire.mp3`),
        },
        {
          id: uuidv4(),
          title: 'Newdawn',
          artist: 'Ben-Sound.com',
          type: 'royalty-free',
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
      if (typeof song.src != 'undefined') {
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
    prev() {
      this.index--;
      if (this.index < 0) {
        this.index = this.songs.length - 1;
      }
      this.play(this.songs[this.index]);
    },
    next() {
      this.index++;
      if (this.index > this.songs.length - 1) {
        this.index = 0;
      }
      this.play(this.songs[this.index]);
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
