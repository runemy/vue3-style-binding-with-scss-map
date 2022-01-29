<template>
  <div class="container">
    <textarea class="form-control" placeholder="Vue3" rows="6" max-rows="12" disabled></textarea>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'StyleBindingVue3',
  setup() {

    const sassColor = ref('red');
    const sassColorBsVar = ref('--bs-red');

    return {
      sassColor, sassColorBsVar
    }
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  @import '@/../node_modules/bootstrap/scss/bootstrap-utilities.scss';

$my-color-map: (
  "pink": $pink,
  "red": $red,
  "orange": $orange,
) !default;

  // // This is working!
  // textarea.form-control {
  //   &:disabled {
  //     background-color: v-bind('sassColor');
  //   }
  // }

  // // This is working!
  // textarea.form-control {
  //   &:disabled {
  //     background-color: map-get($my-color-map, 'red');
  //   }
  // }

  // This is not working :(
  textarea.form-control {
    &:disabled {
      background-color: map-get($my-color-map, v-bind('sassColor'));
    }
  }

  // // This is working!
  // textarea.form-control {
  //   &:disabled {
  //     background-color: var(--bs-red);
  //   }
  // }

  // // This is not working :(
  // textarea.form-control {
  //   &:disabled {
  //     background-color: var(v-bind(sassColorBsVar));
  //   }
  // }

</style>
