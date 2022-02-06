<template>
  <button @click="unmounteComponent()">Desmontando o componente conteúdo</button>
  <Header />
  <Content v-if="visible"/>
</template> 

<script>
import Content from "@/components/layouts/Content.vue";
import Header from "@/components/layouts/Header.vue";

export default {
  name: "App",
  components: {
    Content,
    Header,
  },
  data: () => ({
    visible: true
  }),
  methods: {
    unmounteComponent(){
      this.visible = false
    }
  }
};
</script>

<style>
</style>
