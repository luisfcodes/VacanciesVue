<template>
  <div class="container py-4">
    <div class="row">
      <div class="col">
        <h4>
          Apresente a sua vaga para milhares de profissionais e de graça!!!
        </h4>
      </div>
    </div>

    <div class="row mt-3">
      <div class="col">
        <label class="form-label">Título da vaga</label>
        <input type="text" class="form-control" v-model="title" />
        <div class="form-text">
          Por exemplo: Programador JavaScript e VueJS.
        </div>
      </div>
    </div>

    <div class="row mt-3">
      <div class="col">
        <label class="form-label">Descrição</label>
        <textarea class="form-control" v-model="description"></textarea>
        <div class="form-text">Informe os detalhes da vaga.</div>
      </div>
    </div>

    <div class="row mt-3">
      <div class="col">
        <label class="form-label">Salário</label>
        <input type="number" class="form-control" v-model="salary" />
        <div class="form-text">Informe o salário.</div>
      </div>

      <div class="col">
        <label class="form-label">Modalidade</label>
        <select class="form-select" v-model="modality">
          <option value="" disabled>Selecione uma modalidade</option>
          <option value="1">Home Office</option>
          <option value="2">Presencial</option>
        </select>
        <div class="form-text">Informe a modalidade da vaga.</div>
      </div>

      <div class="col">
        <label class="form-label">Tipo</label>
        <select class="form-select" v-model="type">
          <option value="" disabled>Selecione o tipo de contratação</option>
          <option value="1">CLT</option>
          <option value="2">PJ</option>
        </select>
        <div class="form-text">Informe o tipo de contratação.</div>
      </div>

      <div class="row mt-3">
        <button type="submit" class="btn btn-primary" @click="saveVacancy()">
          Cadastrar
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    title: "",
    description: "",
    salary: "",
    modality: "",
    type: "",
  }),
  methods: {
    saveVacancy() {
      let elapsedTime = Date.now();
      let currentDate = new Date(elapsedTime);

      let vacancies = JSON.parse(localStorage.getItem("vacancies"));

      if (!vacancies) vacancies = [];

      vacancies.push({
        title: this.title,
        description: this.description,
        salary: this.salary,
        modality: this.modality,
        type: this.type,
        postDate: currentDate.toISOString(),
      });

      if (this.validateForm()) {
        localStorage.setItem("vacancies", JSON.stringify(vacancies));

        this.emitter.emit("alert", {
          type: "success",
          title: `A vaga ${this.title} foi cadastrada com sucesso!`,
          description:
            "Parabéns, a vaga está disponível para milhares de profissionais cadastrados na plataforma!!!",
        });

        this.resetForm()
      } else {
        this.emitter.emit("alert", {
          type: "error",
          title: "Ops... Não foi possível cadastrar a vaga.",
          description: "Preencha todos os campos!!!",
        });
      }
    },
    resetForm() {
      (this.title = ""),
      (this.description = ""),
      (this.salary = ""),
      (this.modality = ""),
      (this.type = "");
    },
    validateForm() {
      let valid = true;

      if (this.title === "") valid = false;
      if (this.description === "") valid = false;
      if (this.salary === "") valid = false;
      if (this.modality === "") valid = false;
      if (this.type === "") valid = false;

      return valid;
    },
  },
};
</script>

<style>
</style>