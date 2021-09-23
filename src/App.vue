<template>
  <div id="app">
    <h2>Ejercicio</h2>
    <textarea v-model="message" placeholder="Write your message here" />
    <br />
    <span>{{ message }}</span>
    <br />

    <span v-for="(vowel, index) in message" v-bind:key="index">
      <span v-bind:class="{ red: isVowel({ vowel }) }">{{ vowel }}</span>
    </span>

    <br />
    <span>{{ orderedVowels }}</span>

    <br />
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      message: "",
      vowels: ["a", "A", "e", "E", "i", "I", "o", "O", "u", "U"],
    };
  },
  methods: {
    isVowel: function (vowel) {
      if (this.vowels.includes(vowel.vowel)) {
        return true;
      } else {
        return false;
      }
    },
  },
  computed: {
    orderedVowels: function () {
      var symbols, color;

      var message = Object.assign([], this.message);
      var array = [];
      for (var i = 0; i < message.length; i++) {
        symbols = "0123456789ABCDEF";
        color = "#";

        for (var j = 0; j < 6; j++) {
          color = color + symbols[Math.floor(Math.random() * 16)];
        }
        if (this.vowels.includes(message[i])) {
          array.push({ vowel: message[i], color: color });
        }
      }
      return array;
    },
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
.red {
  color: red;
}
</style>