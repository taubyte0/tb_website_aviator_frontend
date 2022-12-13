<template>
  <JoinPage v-if="joined == false" :iface="loginIface()" />
  <GameOver v-if="gameover == true" :iface="loginIface()" />
  <GameConsole :iface="loginIface()" :game="gameId"/>
</template>

<script>
///https://github.com/neelansh15/vue-connect-wallet
import JoinPage from "./components/JoinPage.vue";
import GameOver from "./components/GameOver.vue";
import GameConsole from "./components/GameConsole.vue";

export default {
  name: "App",
  components: {
    JoinPage,
    GameOver,
    GameConsole,
  },
  data: function () {
    console.log(this.$refs)
    return {
      name: "",
      game: "",
      gameover: false,
      gameId: 1,
    };
  },
  // watch: {
  //   joined() {
  //     this.name;
  //     this.game;
  //   }
  // },
  computed: {
    joined() {  
      return (this.name ? true : false) && (this.game ? true : false);
    },
  },
  methods: {
    loginIface() {
      let vm = this;
      return {
        gameReStarted() {
          vm.gameover = false
          vm.gameId++
        },
        gameIsOver() {
          vm.gameover = true
        },
        joined() {
          return vm.joined;
        },
        set(name, game) {
          vm.name = name;
          vm.game = game;
        },
        get() {
          return {
            name: vm.name,
            game: vm.game,
          };
        },
      };
    },
  },
};
</script>

<style>
#app {
  font-family: Roboto, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
