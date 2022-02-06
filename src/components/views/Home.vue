<template>
  <div class="container py-4">
    <div class="row">
      <div class="col">
        <SearchVacancy />
      </div>
    </div>

    <div class="row mt-5" v-for="(vacancy, index) in vacancies" :key="index">
      <div class="col">
        <Vacancy v-bind="vacancy"/>
      </div>
    </div>

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
import Vacancy from "../comuns/Vacancy.vue";

export default {
  data: () => ({
    vacancies: [
      {
        title: "Analista Programador PHP Pleno",
        description:
          "Profissional com conhecimentos em PHP, Laravel e MySQL. Necessário 3 anos de experiências. Atuará na manutenção de sistemas legados da empresa.",
        salary: 6000,
        modality: "Home Office",
        type: "PJ",
        postDate: "2021-10-10",
      },
      {
        title: "Programador JavaScript Angular",
        description:
          "Profissional com conhecimentos avançados em JavaScript e Angular.",
        salary: 5000,
        modality: "Presencial",
        type: "CLT",
        postDate: "2021-10-07",
      },
      {
        title: "Programador JavaScript Vue",
        description:
          "Profissional com conhecimentos avançados em JavaScript e Vue.",
        salary: 5000,
        modality: "Home Office",
        type: "CLT",
        postDate: "2021-10-06",
      },
      {
        title: "Analista de Banco de Dados Sênior",
        description:
          "Domínio dos bancos de dados SQL Server, Oracle, Postgre e MySQL",
        salary: 9000,
        modality: "Presencial",
        type: "PJ",
        postDate: "2021-10-06",
      },
      {
        title: "Programador Web Júnior",
        description:
          "Conhecimentos básicos em HTML, CSS, JavaScript, Bootstrap, PHP e MySQL",
        salary: 3000,
        modality: "Presencial",
        type: "CLT",
        postDate: "2021-10-05",
      },
    ],
  }),
  components: {
    SearchVacancy,
    Indicator,
    Vacancy,
  },
};
</script>