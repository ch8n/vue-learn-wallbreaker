<template>
  <div id="app">
    <h1>{{ msg }}</h1>

    <div id="wall" :class="{endwall:isEnded}"></div>
    <div id="wall-health">
      <div :style="{width:health+'%'}"></div>
    </div>

    <div id="controls">
      <button @click="punch">Punch</button>
      <button @click="restart" v-show="isEnded">Restart</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      msg: "Welcome to Wall breaking App",
      health: 100,
      isEnded: false
    };
  },
  methods: {
    punch() {
      this.health -= 10;
      if (this.health <= 0) {
        this.isEnded = true;
      }
    },
    restart() {
      this.health = 100;
      this.isEnded = false;
    }
  },
  computed: {}
};
</script>

<style>
#wall {
  width: 200px;
  height: 500px;
  margin: 0 auto;
  background: url(/src/img/wallok.jpeg) center no-repeat;
  background-size: 300%;
}
#wall.endwall {
  width: 200px;
  height: 500px;
  margin: 0 auto;
  background: url(/src/img/wallend.jpeg) center no-repeat;
  background-size: 180%;
}
#wall-health {
  width: 200px;
  border: 2px solid #000;
  margin: 0 auto 20px auto;
}

#wall-health div {
  height: 40px;
  background: crimson;
}
#controls {
  width: 120px;
  margin: 0 auto;
}
</style>
