<template>
  <div :class="alertStyle" role="alert">
    <slot name="title"></slot>
    <hr>
    <slot name="description"></slot>
  </div>
</template>

<script>
export default {
  props: {
    type: String
  },
  computed: {
    alertStyle(){
      switch(this.type){
        case 'success': return 'alert alert-success'
        case 'error': return 'alert alert-danger'
      }
      return ''
    }
  }
};
</script>
