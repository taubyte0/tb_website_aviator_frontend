<template>
  <section class="vh-100 gradient-custom">
    <div class="container py-5 h-100">
      <div class="row d-flex justify-content-center align-items-center h-100">
        <div class="col-12 col-md-8 col-lg-6 col-xl-5">
          <div class="card bg-dark text-white" style="opacity: .5; border-radius: 1rem">
            <div class="card-body p-5 text-center">
              <div class="mb-md-5 mt-md-4">
                <h2 class="fw-bold mb-2 text-uppercase">Join a Game</h2>
                <p class="text-white-50 mb-5">
                  Enter your Name and the Group your want to join/create
                </p>

                <div class="form-outline form-white mb-4">
                  <input
                    type="text"
                    id="typeEmailX"
                    class="form-control form-control-lg"
                    v-model="name"
                  />
                  <label v-if="!name" class="form-label" for="typeEmailX">Name</label>
                </div>

                <div class="form-outline form-white mb-4">
                  <input
                    type="text"
                    id="typePasswordX"
                    class="form-control form-control-lg"
                    v-model="game"
                  />
                  <label v-if="!game" class="form-label" for="typePasswordX">Group</label>
                </div>

                <button class="btn btn-outline-light btn-lg px-5" type="submit" @click="close()">
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
export default {
  name: "LoginPage",
  props: [ "iface" ],
  data: function() {
    return {
      name: "",
      game: ""
    }
  },
  mounted() {
    let obj = this.iface.get()
    this.name = obj.name
    this.game = obj.game
  },
  methods: {
    close: function(){
      console.log(this.name, this.game)
      this.iface.set(this.name, this.game)
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
