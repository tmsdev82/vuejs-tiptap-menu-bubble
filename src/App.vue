<template>
<div id="app">
    <menu-bubble :propContent="fileContent" />
    <file-reader @load="fileContent = $event"></file-reader>
</div>
</template>

<script>
import MenuBubble from './components/MenuBubble.vue'
import FileReader from './components/FileReader'

export default {
    name: 'App',
    components: {
        MenuBubble,
        FileReader
    },
    data() {
        return {
            fileContent: ""
        }
    }
}
</script>

<style lang="sass">
@import './assets/sass/main.scss'
</style>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
