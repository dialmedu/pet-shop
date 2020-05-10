<template>
    <header>
       <Top />
       <Bottom />
    </header>
</template>

<script>
    import Vue from 'vue'
    import Top from './top'
    import Bottom from './bottom'

    export default Vue.extend({
     
        components: {
            Top,
            Bottom
        }
    })
</script>

<style>
    header{
        color: white;
        display: flex;
        flex-direction: column;
        font-size: .9em;
        height: auto;
    }

    header a,
    header li,
    header span{
        color: white;
    }
</style>