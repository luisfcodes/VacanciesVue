<template>
  <div>
    <keep-alive>
      <component :is="content" />
    </keep-alive>

  </div>
</template>

<script>

import Home from '../views/Home.vue'
import PostVacancy from '../views/PostVacancy.vue'

export default {
  props: {
    content: {
      type: String,
      required: true
    }
  },
  components: {
    Home,
    PostVacancy
  },
  // beforeCreate(){
  //   console.log("Antes de criar", this.test)
  // },
  // created(){
  //   console.log('Criado', this.test)
  // },
  // beforeMount(){
  //   console.log('Antes de ser montado')
  // }, 
  // mounted(){
  //   console.log('Montado')
  // },
  // beforeUpdate(){
  //   console.log('Antes de ser atualizado')
  // },
  // updated(){
  //   console.log("Atualizado")
  // },
  // beforeUnmount(){
  //   console.log('Antes de ser desmontado')
  // },
  // unmounted(){
  //   console.log('Desmontado')
  // },
  // errorCaptured(){
  //   console.log('Erro capturado')
  // },
  // renderTracked(){
  //   console.log('re-renderização rastreada')
  // },
  // renderTriggered(){
  //   console.log('re-renderização ativada')
  // },
  // activated(){
  //   console.log('Componente ativado')
  // },
  // deactivated(){
  //   console.log('Componente desativado')
  // }
}

</script>

