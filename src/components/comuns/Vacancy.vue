<template>
  <div class="card">
    <div class="card-header bg-dark text-white">
      <div class="row">
        <div class="col d-flex justify-content-between">
          <div>{{ title }}</div>
          <div>
            <div class="form-check form-switch">
              <input class="form-check-input" type="checkbox" v-model="favorited">
              <label class="form-check-label">Favoritar</label>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="card-body">
      <p>{{ description }}</p>
    </div>
    <div class="card-footer">
      <small class="text-muted"
        >Salário: R${{ salary }} | Modalidade: {{ getModality }} | Tipo:
        {{ getType }} | Publicação: {{ getDate }}</small
      >
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
      validator(props) {
        if (props.length < 4) {
          return false;
        } else {
          return true;
        }
      },
      default: "Sem título",
    },
    description: String,
    salary: Number,
    modality: String,
    type: String,
    postDate: String,
  },
  data: () => ({
    favorited: false
  }),
  watch: {
    favorited(newValue){
      if(newValue){
        this.emitter.emit('favoriteVacancy', this.title)
      }else{
        this.emitter.emit('disfavorVacancy', this.title)
      }
    }
  },
  methods: {
  },
  computed: {
    getModality() {
      switch (this.modality) {
        case "1":
          return "Home Office";
        case "2":
          return "Presencial";
      }
      return ''
    },
    getType() {
      switch (this.type) {
        case "1":
          return "CLT";
        case "2":
          return "PJ";
      }
      return ''
    },
    getDate(){
     let localDate = new Date(this.postDate)
     return localDate.toLocaleDateString('pt-BR')
    }
  },
};
</script>
