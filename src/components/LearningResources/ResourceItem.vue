
<!-- 
单个物品的展示 
被包在base-card中；
展示各种属性； 
-->


<template>
    <base-card>
        <li> 
            <div>
                <h2>学习资料为:{{ learnR.title }}</h2>
            </div>
            <nav> <a :href=" learnR.link ">学习链接</a> </nav>
            <p>介绍:{{ learnR.description }}</p>
            
            <base-button mode="flat" :type="button" @click="deleteResource(learnR.id)"> 删除</base-button>
            
            <!-- <h2>一个展示 {{ aaa }}</h2> -->
        </li>
    </base-card>
</template>

<script>

export default {
    props:[
        'learnR', 
        'aaa', // just for text
    ],
    inject:[
      'deleteResource',
    ],
}

</script>

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #ce5c00;
}

a:hover,
a:active {
  color: #c89300;
}
</style>