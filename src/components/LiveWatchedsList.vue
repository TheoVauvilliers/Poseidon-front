<template>
  <div class="liveWatched-list">
    <ul>
      <li v-for="(liveWatched, index) in liveWatcheds" :key="index">
        {{ index }}. Watched <span>{{ liveWatched.name }}</span> at <span>{{ liveWatched.watchedAt }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  props: {
      liveWatcheds: {
          type: Array,
          required: true
      }
  }
});
</script>

<style scoped>
  .liveWatched-list {
    max-width: 960px;
    margin: 40px auto;
  }
  .liveWatched-list ul {
    padding: 0;
  }
  .liveWatched-list li {
    list-style-type: none;
    padding: 16px;
    margin: 16px 0;
    background-color: #1A1A1A;
  }
  .liveWatched-list span {
    font-style: italic;
    color: wheat;
  }
</style>