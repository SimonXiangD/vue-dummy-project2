<template>

    <the-header :title="pageTitle"></the-header>
    <the-resources></the-resources>


</template>

<script>

import TheHeader from './components/Layouts/TheHeader.vue';
import TheResources from './components/LearningResources/TheResources.vue';


export default {
    components:{
        
        TheHeader,
        TheResources,

    },
    data() {
        return {
            pageTitle: '平平无奇的标题',
        }
    }
}

</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}

#mainResourceList {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>