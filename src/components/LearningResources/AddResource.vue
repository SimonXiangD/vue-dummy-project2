<template>

        <base-log v-if="isInvalidInput" title="提示" @closeDialog="confirmError">
            <template #default>
                <p>抱歉，你输入的信息有一些误差。</p>
                <p>请确保不要空出信息。</p>
            </template>
            <template #menu>
                <base-button @click="cofirmError">确定</base-button>
            </template>
        </base-log>
    
        <base-card>

            <h2>添加物品！</h2>

            <form @submit.prevent="submitData">

          
                <label for="title">标题</label>
                <input type="text" id="title" ref="titleInput"  class="form-control" >
             

                <label for="description">描述</label>
                <input type="text" id="description" ref="descriptionInput" class="form-control"  >

                <label for="link">链接</label>
                <input type="text" id="link" ref="linkInput" class="form-control"  >

                <base-button type="submit" mode="flat">提交</base-button>
            </form>
        </base-card>
</template>

<script>
export default {
    inject:[
        'addResource'
    ],

    data()  {
        return {
            isInvalidInput : false,
        };
    },

    methods: {
        submitData() {
            const title = this.$refs.titleInput.value;
            const description = this.$refs.descriptionInput.value;
            const link = this.$refs.linkInput.value;
            
            if(
                title.trim() === '' || 
                description.trim() === '' || 
                link.trim() === '' 
            ) {
                this.isInvalidInput = true;
                return ;
            }

            this.addResource(title, description, link);
        },

        confirmError() {
            this.isInvalidInput = false;
        }
    }

}
</script>


<style scoped>

label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}

</style>