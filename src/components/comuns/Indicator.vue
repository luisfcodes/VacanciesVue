<template>
  <div class="col-4">
    <div :class="style">
      <p>{{ title }}</p>
      <h2>{{ indicator }}</h2>
    </div>
  </div>
</template>

<script>

export default {
  props: ["title", "indicator", "bg", "color"],
  computed: {
    style(){
      return `h-100 p-5 rounded-3 border ${this.bg} ${this.color}`
    }
  }
};
</script>
