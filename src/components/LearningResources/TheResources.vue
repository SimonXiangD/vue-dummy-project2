<template>

<base-card>
    <base-button 
    @click="changeSelectedStatus('stored-resources')"
    :mode="changeButtonMode('stored-resources')"
    >资源列表</base-button>

    <base-button 
    @click="changeSelectedStatus('add-resource')"
    :mode="changeButtonMode('add-resource')"
    >添加资源</base-button>
</base-card>
<keep-alive>
 <component :is="selectedStatus"></component>
</keep-alive>
</template>


<script>

import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';

export default {

    components:{
        StoredResources, 
        AddResource,
    },

    data() {
        return {
            selectedStatus : 'stored-resources',

            selectedButton : 'stored-resources',

            learningResource: [
                {
                    id:'official-guide',
                    title:'vue official guide',
                    description:'The official guide for vue3.',
                    link:'https://vuejs.org/',
                },
                {
                    id:'official-guide',
                    title:'vue official guide',
                    description:'The official guide for vue3.',
                    link:'https://vuejs.org/',
                },
            ],

        };
    },

    provide() {
        return {
            learningResource: this.learningResource,
            addResource: this.createResource,
            deleteResource: this.deleteResource,
        }
    },

    methods:{
        changeSelectedStatus(value) {
            this.selectedStatus = value;
        },

        changeButtonMode(value) {
            return value === this.selectedStatus ? 'null' : 'flat';
        },

        createResource(title, description, link) {
            const newR = {
                id: new Date().toISOString(),
                title:title,
                description:description,
                link:link,
            }
            this.learningResource.unshift(newR);
            this.selectedStatus = 'stored-resources';
        },

        deleteResource(id) {
            const deleteIndex = this.learningResource.findIndex((learnR)=> learnR.id === id );
            this.learningResource.splice(deleteIndex, 1);
        }
    }
}

</script>