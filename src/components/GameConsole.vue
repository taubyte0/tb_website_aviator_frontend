<template>
  <div class="game-holder" id="gameHolder">
    <button
      class="startbtn btn btn-outline-light btn-lg px-5"
      type="submit"
      v-if="playing == false && iface.joined() == true"
      @click="start()"
    >
      Start
    </button>

    <div class="header">
      <h1><span>the</span>Aviator</h1>
      <h2>fly it to the end</h2>
      <div class="score" id="score">
        <div class="score__content" id="dist">
          <div class="score__label">distance</div>
          <div class="score__value score__value--dist" id="distValue">000</div>
        </div>
        <div class="score__content" id="energy">
          <div class="score__label">energy</div>
          <div class="score__value score__value--energy" id="energyValue">
            <div class="energy-bar" id="energyBar"></div>
          </div>
        </div>
      </div>
    </div>
    <div class="world" id="world"></div>
  </div>
</template>

<script>
import {game, sea, sky, gameContainer, resetGame, newGame, gameLoop} from "../js/game.js";

import "../assets/css/game.css"

export default {
  name: "GameConsole",
  props: ["iface", "game"],
  data: function () {
    return {
      playing: game ? game.status == "playing" : false,
      gameover: game ? game.status == "gameover" : false,
    };
  },
  watch: {
    game() {
      this.restart();
    },
  },
  methods: {
    start() {
      this.playing = true;
      game.status = "playing";
    },
    restart() {
      this.playing = false;
      this.gameover = false;
      sea.mesh.position.y = -game.seaRadius;
      sky.mesh.position.y = -game.seaRadius;
      resetGame();
    },
    gameIsOver() {
      this.gameover = true;
      this.iface.gameIsOver();
    },
  },
  mounted: function () {
    gameContainer(this)
    newGame()
    gameLoop();
  },
};
</script>

