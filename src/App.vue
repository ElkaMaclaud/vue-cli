<template>
  <div class='container pt-1'>
    <div class='card'>
      <h2>Slots</h2>
    </div>

    <app-block>
      <p>Это самый важный текст для нового блока</p>

      <template #header>
        <h3>Это заголовок!</h3>
      </template>

      <template v-slot:footer>
        <hr />
        <small>Это footer</small>
      </template>
    </app-block>
  </div>
</template>

<script>
import AppBlock from './AppBlock.vue'

export default {
  mounted() {
    console.log(this.$slots)
  },
  components: {
    // 'app-news': AppNews
    AppBlock
  }
}
</script>

<style scoped></style>
