<template>
<icon name="bold" size="large" />
</template>

<script>
import Icon from './Icon.vue'

export default {
    name: 'HelloWorld',
    components: {
        Icon
    },
    props: {
        msg: String
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>

</style>
