<template>
  <div class='container pt-1'>
    <div class='card'>
      <h2>Динамические и асинхронные компоненты</h2>

      <app-button :color="oneColor" @action="active = 'one'">One</app-button>
      <app-button :color="twoColor" @action="active = 'two'">Two</app-button>
    </div>

    <!-- <app-text-one v-if="active==='one'"></app-text-one>
    <app-text-two v-else-if="active==='two'"></app-text-two> -->

    <keep-alive>
      <component :is="componentName"></component>
    </keep-alive>

  </div>
</template>
<script>
import AppButton from './AppButton.vue'
import AppTextOne from './AppTextOne.vue'
import AppTextTwo from './AppTextTwo.vue'

export default {
  data() {
    return {
      active: 'one' // two
    }
  },
  computed: {
    componentName() {
      // if (this.active === 'one') {
      //   return 'app-text-one'
      // }
      // return 'app-text-two'
      return 'app-text-' + this.active
    },
    oneColor() {
      return this.active === 'one' ? 'primary' : ''
    },
    twoColor() {
      return this.active === 'two' ? 'primary' : ''
    }
  },
  components: {
    AppButton,
    AppTextOne,
    AppTextTwo
  }
}
</script>
