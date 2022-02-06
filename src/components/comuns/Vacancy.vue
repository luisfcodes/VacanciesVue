<template>
  <div class="card">
    <div class="card-header bg-dark text-white">{{title}}</div>
    <div class="card-body">
      <p>{{description}}</p>
    </div>
    <div class="card-footer">
      <small class="text-muted">Salário: R${{salary}} | Modalidade: {{modality}} | Tipo: {{type}} | Publicação: {{postDate}}</small>
    </div>
  </div>
</template>

<script>

export default {
  props: {
    title: {
      type: String,
      required: true,
      validator(props){
        if(props.length < 4){
          return false
        } else {
          return true
        }
      },
      default: 'Sem título'
    },
    description: String,
    salary: Number,
    modality: String,
    type: String,
    postDate: String
  }
}

</script>
