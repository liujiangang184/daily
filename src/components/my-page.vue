<template>
    <div>
        <ul class="pages">
            <li :class="{active:current==i}" v-for="i in pageNumber" :key="i" @click="pagechange(i)">{{i}}</li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "my-page",
        props: {
            total: {
                required: true,
                type: Number,
            },
            pageSize: {
                type: Number,
                default: 3,
            }
        },
        computed:{
            pageNumber(){
                return  Math.ceil(this.total / this.pageSize);

            }
        },
        data() {
            return {
                current:1
            }
        },
        methods:{
            pagechange(i){
                if(this.current==i){
                    return
                }
                this.current = i;
                this.$emit('changepage',i)
            }
        }
    }
</script>

<style scoped>
    .pages{
        width: 100%;
        height: 30px;
        display: flex;
    }
    .pages > li{
        width: 30px;
        height: 28px;
        text-align: center;
        margin-left: 10px;
        line-height: 28px;
        border-radius: 3px;
        background-color: #ddd;
        cursor: pointer;
    }
    .pages > li.active{
        background-color: #4094fe;
        color: white;
    }
</style>