<template>
    <div class="panel " :class="'panel-'+scene">
     <!-- <slot name="header">后备插槽</slot>
        <ul class="list-group">-->
            <li class="list-group-item" v-for="item in inserts"
                :key="item.id" content="item.content" >{{item.content}}
                <!--<input type="checkbox" v-model="item.stats">-->
            </li>
            <my-li class="list-group-item" v-for="item in list"
                   :key="item.id" :content="item.content" :status="item.status"
                   :id="item.id" @listdelete="listdelete(item.id)"
            ></my-li>
          <!--  <slot msg="hello" :scene="scene"></slot>
            <template v-slot：default="props">
                <div>{{props.msg}}{{props.scene}}</div>
            </template>
            <li></li>
            <li></li>
            <li></li>
        </ul>
        <slot name="footer">第二个</slot>-->
    </div>
</template>

<script>
    import MyLi from '../components/my-li'
    export default {
        name: "my-button",
        props: {
            list: {
                required: true,
                type: Array,
            },
            scene:{
                type:String,
                default:'info'
            },
            title:{
                type:String,
            }
        },
        components:{
            MyLi
        },
        methods:{
            listdelete(id){
                this.$emit('indexdelete',id)
            }
        }
    }
</script>

<style scoped>
    @import url("https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css");
</style>