<template>
    <div>
        <my-btn type="primary" title="成功" :num="number"
        @zs="updatenumer"
        ></my-btn>
        <my-btn type="primary" title="成功" :num="number"
                @zs="updatenumer"
        ></my-btn>
        <my-btn type="primary" title="成功" :num="number"
                @zs="updatenumer"
        ></my-btn>
       <!-- <my-btn type="danger" :num="number"></my-btn>
        <my-btn :num="number"></my-btn>-->
    </div>
</template>

<script>
    import MyBtn from '../components/my-btn'

    export default {
        name: "write",

        data:function(){
          return{
              info:'danger',
              number:10
          }
        },
        methods:{
          updatenumer(){
              this.number++;
          }
        },
        components: {
            MyBtn
        }
    }
</script>

<style scoped>
    @import url("https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css");
</style>