<template>
  <div class="container py-4">
    <div class="row">
      <div class="col">
        <SearchVacancy />
      </div>
    </div>

    <vacancies-list />

    <div class="row mt-5">
      <Indicator
        title="Vagas abertas"
        indicator="100"
        bg="bg-primary"
        color="text-white"
      />

      <Indicator
        title="Profissionais cadastrados"
        indicator="225"
        bg="bg-dark"
        color="text-white"
      />

      <Indicator
        title="Visitantes online"
        indicator="23"
        bg="bg-success"
        color="text-white"
      />
    </div>
  </div>
</template>

<script>
import SearchVacancy from "../comuns/SearchVacancy.vue";
import Indicator from "../comuns/Indicator.vue";
import VacanciesList from '../comuns/VacanciesList.vue'

export default {
  components: {
    SearchVacancy,
    Indicator,
    VacanciesList
  },
};
</script>