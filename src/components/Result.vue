<template>
  <div :v-if="results.length">
    <p>{{ results.word }}</p>
    <ul>
      <li v-for="item in results.meanings" :key="item.partOfSpeech">
        <span>{{ item.partOfSpeech }}</span>
        <span> / </span>
        <span>{{ item.definitions[0].definition }}</span>
      </li>
    </ul>
    <p>{{ results.origin }}</p>
    <ul>
      <li v-for="phonetic in results.phonetics" :key="phonetic.text">
        <p>{{ phonetic.text }} /</p>

        <audio controls>
          <source :src="phonetic.audio" type="audio/mpeg" />
          Your browser does not support the audio element.
        </audio>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['results'],
};
</script>

<style></style>
