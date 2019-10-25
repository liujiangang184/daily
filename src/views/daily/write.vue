<template>
    <div>
        <el-form :model="daily" ref="daily">
            <el-form-item label="座右铭">
                <el-input v-model="daily.motto" placeholder="" minlength="10" maxlength="50"
                show-word-limit=""></el-input>
            </el-form-item>
            <el-form-item label="完成情况">
                <el-input v-model="daily.finish" placeholder="请输入内容"
                          ></el-input>
            </el-form-item>
            <el-form-item label="完成内容">
                <el-input
                        placeholder="请输入内容"
                        v-model="daily.content"
                        minlength="10"
                ></el-input>
            </el-form-item>
            <el-form-item label="心得体会">
                <el-input
                        placeholder="请输入内容"
                        v-model="daily.feeling"
                        minlength="10"
                ></el-input>
            </el-form-item>
            <el-form-item label="遇到问题">
                <el-input
                        placeholder="请输入内容"
                        v-model="daily.problem"
                ></el-input>
            </el-form-item>
            <el-form-item label="建议">
                <el-input
                        placeholder="请输入内容"
                        v-model="daily.suggest"
                ></el-input>
            </el-form-item>
            <el-form-item label="其他">
                <el-input
                        placeholder="请输入内容"
                        v-model="daily.other"
                ></el-input>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="submitDaily">提交</el-button>
            </el-form-item>
        </el-form>
    </div>
</template>

<script>
    export default {
        name: "write",
        data(){
            return{
                daily:{
                    names:'',
                    classes:'wuif1907-2',
                    motto:'',  /*座右铭*/
                    content:'',
                    finish:'',
                    problem:'',
                    feeling:'',
                    suggest:'',
                    other:''
                },
            rules: {
                name: [
                    { require:true, trigger: 'blur' ,message:'用户名不可以为空'},
                    {min:2,max:10,message:'请输入3-10个字符',trigger:'blur'}
                ],
                    motto: [
                    {  trigger: 'blur',require:true,message:'座右铭不可以为空' }
                ],
                    classes: [
                    {require:true,trigger:'change',message:'班级不可以为空'}
                ],
                    content: [
                    {require:true,trigger:'blur',message:'学习内容不可以为空'},

                ],
                    feeling:[
                    {require:true,trigger:'blur',message:'心得体会不可以为空',},
                ],

            }
        }
    },
    methods:{
        submitDaily(){
            this.daily.names = JSON.parse(localStorage.user).username;

            fetch('http://www.daily-end.com/index/index/index',{
                method:'POST',
                body:JSON.stringify(this.daily),
                headers:new Headers({
                    'Content-type':'application/json'
                })
            }).then(res=>res.json()).then(data=>{
                if (data.code == 200){
                    this.message.success(data.msg)
                    this.$refs.daily.resetFields();
                    alert('提交成功')
                }else {
                    this.message.error(data.msg)
                }
            })
        },
    }
    }
</script>

<style scoped>
    .el-textarea__inner{
        resize: none;
    }
    .el-input{

    }
</style>