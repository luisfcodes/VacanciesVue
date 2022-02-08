<template>
  <div>
    <div class="buttonFav">
      <button
        class="btn btn-primary"
        type="button"
        data-bs-toggle="offcanvas"
        data-bs-target="#offcanvasRight"
        aria-controls="offcanvasRight"
      >
        Vagas Favoritas
      </button>
    </div>

    <div
      class="offcanvas offcanvas-end"
      tabindex="-1"
      id="offcanvasRight"
      aria-labelledby="offcanvasRightLabel"
    >
      <div class="offcanvas-header">
        <h5 id="offcanvasRightLabel">Vagas Favoritadas</h5>
        <button
          type="button"
          class="btn-close text-reset"
          data-bs-dismiss="offcanvas"
          aria-label="Close"
        ></button>
      </div>
      <div class="offcanvas-body">
        <ul class="list-group">
          <li class="list-group-item" v-for="(vacancy, index) in vacancies" :key="index">{{vacancy}}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    vacancies: []
  }),
  mounted(){
    this.emitter.on('favoriteVacancy', (title) => {
      this.vacancies.push(title)
    })

    this.emitter.on('disfavorVacancy', (title) => {
      let indexArray = this.vacancies.indexOf(title)
      if(indexArray !== -1) this.vacancies.splice(indexArray, 1)
    })
  }
};
</script>

<style scoped>
.buttonFav {
  position: absolute;
  z-index: 1;
  top: 70px;
  right: 0px;
}
</style>
