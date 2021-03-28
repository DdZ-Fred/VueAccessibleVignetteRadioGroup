<template>
  <div id="app">
    <div>
      <vignette-radio-group
        cid="music-genre-field"
        label="Select a music genre"
        :items="items"
      ></vignette-radio-group>
    </div>
  </div>
</template>

<script>
import VignetteRadioGroup from "./components/VignetteRadioGroup";

export default {
  name: "App",
  components: { VignetteRadioGroup },
  data() {
    return {
      items: [
        {
          label: "Metal",
          value: "metal",
          url: "https://picsum.photos/200",
        },
        {
          label: "Jazz",
          value: "jazz",
          url: "https://picsum.photos/200",
        },
        {
          label: "Classical",
          value: "classical",
          url: "https://picsum.photos/200",
        },
        {
          label: "Rap",
          value: "rap",
          url: "https://picsum.photos/200",
        },
        {
          label: "Rock",
          value: "rock",
          url: "https://picsum.photos/200",
        },
      ],
    };
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
