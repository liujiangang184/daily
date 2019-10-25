<template>
    <button :class="['btn','btn-'+type]" @click="countclick">{{title}}{{num}}</button>
</template>

<script>
    export default {
        name: "my-btn",
        /*props:['type','title'],*/
        props:{
            type:{
                default:'primary'
            }  ,
            title:{
                default: '这是一个默认的按钮'
            },
            num:{
                // type:Number,
                required:true
            }
        },
        data:function () {
            return{
               count:this.num,
                msg:'my-btn'
            }
        },
        methods:{
            countclick(){
                this.$emit('zs');
            }
        },
     /*   computed:{
            uppermsg(){
                this.msg.charAt(0).toUpperCase()+this.msg.substring(1);
            }
        }*/
    }
</script>

<style scoped>
.btn-info{
    margin-left: 20px;
}
</style>