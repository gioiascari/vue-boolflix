<template>
  <div class="bg-black p-3">
    <div class="container-lg">
      <div class="row">
        <div class="col-lg-6 col-md-8 d-flex justify-content-around flex-wrap">
          <!-- LOGO -->
          <h1 class="text-danger m-0">BoolFlix</h1>
          <!-- /LOGO -->
          <!-- MENU -->
          <ul class="d-flex gx_5 m-0 align-items-center">
            <li><a class="mx-2 text-light m-3" href="">Home</a></li>
            <li>
              <a class="mx-2 text-light" href="serie">Serie Tv</a>
            </li>
            <li><a class="mx-2 text-light" href="film">Films</a></li>
            <li><a class="mx-2 text-light" href="lista">La mia lista</a></li>
          </ul>
          <!-- / MENU -->
        </div>

        <div class="col-md-4 col-lg-6 d-flex justify-content-end flex-wrap">
          <div class="input">
            <div class="input-group m-0">
              <!-- INPUT-BUTTON più logica -->
              <input
                type="text"
                class="form-control"
                placeholder="Search something"
                aria-label="Recipient's username"
                aria-describedby="button-addon2"
                v-model="searchMovie"
                @keyup.enter="startSearch"
              />
              <button
                class="btn btn-outline-dark btn bg-danger"
                @click.prevent="startSearch"
                type="button"
                id="button-addon2"
              >
                <i class="bi bi-search"></i>
              </button>
              <!-- /INPUT-BUTTON più logica -->
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MyHeader",
  components: {},
  data() {
    return {
      searchMovie: "",
    };
  },
  methods: {
    startSearch() {
      this.$emit("searchArguments", this.searchMovie);
      console.log(this.searchMovie);
    },
  },
};
</script>

<style lang="scss">
@import "@/style/utilities";
ul {
  list-style-type: none;
  li a:hover {
    text-decoration: underline;
    padding: 5px;
    background-color: rgba(255, 0, 0, 0.517);

    border-radius: 10px;
  }
  a {
    text-decoration: none;
  }
}
.gx_5 {
  column-gap: 20px;
}
</style>
