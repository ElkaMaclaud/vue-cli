<template lang="">
    <hr />
    <ul>
        <li v-for="item in news" :key="item">{{ item.title }}</li>
    </ul>
</template>
<script>
export default {

}
</script>
<style lang="">

</style>
