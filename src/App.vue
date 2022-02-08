<template>
  <FavoriteVacancies />
  <Header @navigate="component = $event"/>
  <Alert v-if="showAlert" :type="alert.type">
    <template v-slot:title><h5>{{ alert.title }}</h5></template>
    <template v-slot:description><p>{{ alert.description }}</p></template>
  </Alert>
  <Content :content="component"/>
</template> 

<script>
import Content from "./components/layouts/Content.vue";
import Header from "./components/layouts/Header.vue";
import FavoriteVacancies from './components/comuns/FavoriteVacancies.vue';
import Alert from './components/comuns/Alert.vue'

export default {
  name: "App",
  components: {
    Content,
    Header,
    FavoriteVacancies,
    Alert
  },
  data: () => ({
    component: 'Home',
    showAlert: false,
    alert: {title: '', description: '', type: ''}
  }),
  mounted(){
    this.emitter.on('alert', (p) => {
      this.alert = p
      this.showAlert = true
      setTimeout(() => this.showAlert = false,4000)
    })
  }
};
</script>

<style>
</style>
