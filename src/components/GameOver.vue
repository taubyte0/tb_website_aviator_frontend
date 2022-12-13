<template>
  <section class="vh-100 gradient-custom">
    <div class="container py-5 h-100">
      <div class="row d-flex justify-content-center align-items-center h-100">
        <div class="col-12 col-md-8 col-lg-6 col-xl-5">
          <div class="card bg-dark text-white" style="opacity: .5; border-radius: 1rem">
            <div class="card-body p-5 text-center">
              <div class="mb-md-5 mt-md-4">
                <h2 class="fw-bold mb-2 text-uppercase">{{ distance() }}</h2>
                <p class="text-white-50 mb-5">
                  Enter your Name and the Board your want to join/create
                </p>

                

                <button class="btn btn-outline-light btn-lg px-5" type="submit" @click="restart()">
                  Join/Create
                </button>

                
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import {game} from "../js/game.js";


export default {
  name: "GameOver",
  props: [ "iface" ],
  data: function() {
    return {
      
    }
  },
  mounted() {
  },
  methods: {
    distance(){
      return Math.ceil(game.distance)
    },
    restart(){
      this.iface.gameReStarted()
    },
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.gradient-custom {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  backdrop-filter: blur(3px);
}
</style>
