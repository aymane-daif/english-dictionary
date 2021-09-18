<template>
  <div v-if="results.length" class="results">
    <p class="word">{{ results[0].word }}</p>
    <ul class="phonetic">
      <li v-for="phonetic in results[0].phonetics" :key="phonetic.text">
        <p>{{ phonetic.text }}</p>
        <audio controls ref="audio">
          <source :src="phonetic.audio" type="audio/mpeg" />
          Your browser does not support the audio element.
        </audio>
      </li>
      <img
        class="audio-icon"
        src="../assets/volume.svg"
        alt="volume"
        @click="playSound"
      />
    </ul>
    <ul>
      <li
        v-for="item in results[0].meanings"
        :key="item.partOfSpeech"
        class="definition"
      >
        <span>{{ item.partOfSpeech }}</span>
        <span> / </span>
        <span>{{ item.definitions[0].definition }}</span>
      </li>
    </ul>
    <div class="origin" v-if="results[0].origin">
      <span>Origin: </span>
      <span>{{ results[0].origin }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: ['results'],
  methods: {
    playSound() {
      const audioEl = this.$refs.audio;
      audioEl.currentTime = 0;
      audioEl.play();
    },
  },
};
</script>

<style>
.results > * {
  margin: 1.5rem auto;
  width: 80%;
}
.results .word {
  font-size: 2.75rem;
  font-weight: 600;
  text-transform: capitalize;
  letter-spacing: 1px;
}
.results .definition {
  font-style: italic;
  font-weight: 800;
}
.results .origin {
  background: #f2f2f2;
  border-radius: 11px;
  padding: 1.5rem;
  line-height: 1.8rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
}
.results .origin span:first-child {
  font-weight: 800;
}
.results .phonetic {
  font-weight: 600;
  background: #ffffff;
  width: 100px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: auto;
  padding: 1.25rem;
  border-radius: 10px;
}
.results .phonetic audio {
  display: none;
}
.results .phonetic .audio-icon {
  cursor: pointer;
  margin-top: 10px;
}
</style>
