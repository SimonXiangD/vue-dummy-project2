<!-- 
存储了所有物品，并进行展示
 -->


<template>


    
    <ul id="mainResourceList" >
        <resource-item 
        v-for="learnR in learningResource" :key="learnR.id" 
            :learnR = "learnR"
            :aaa="learnR.description"
        ></resource-item>
    </ul>

</template>

<script>

import ResourceItem from './ResourceItem.vue';


export default {
    inject:['learningResource'],
    components:{
        ResourceItem,
    }
}

</script>