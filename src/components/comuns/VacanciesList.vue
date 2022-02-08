<template>
  <slot attOne="Primeiro atributo" :attTwo="[1,2,3,4]">
    <div class="row mt-5" v-for="(vacancy, index) in vacancies" :key="index">
      <div class="col">
        <Vacancy v-bind="vacancy"/>
      </div>
    </div>
  </slot>
</template>

<script>

  import Vacancy from './Vacancy.vue'

export default{
  data: () => ({
    vacancies: []
  }),
  components: {
    Vacancy
  },
  activated(){
    this.vacancies = JSON.parse(localStorage.getItem('vacancies'))
  },
  mounted(){
    this.emitter.on('filterVacancy', vacancy => {

      const vacancies = JSON.parse(localStorage.getItem('vacancies'))
      const filteredVacancies = vacancies.filter(item => {
        return item.title.toLowerCase().includes(vacancy.title.toLowerCase())
      })
      
      this.vacancies = filteredVacancies
    })
  }
}
</script>
