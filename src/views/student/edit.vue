<template>
    <div>
        <!--<el-breadcrumb>

        </el-breadcrumb>
        <el-divider></el-divider>-->
        <div class="form" v-if="form"></div>
        <el-form :model="form" ref="form" label-width="80px" :roles="roles">
            <el-form-item label="姓名" porp="username">
                <el-input v-model="form.username" placeholder="Username" clearable="" style="width: 500px">
                    <i slot="prefix" class="el-input__icon el-icon-user"></i>
                </el-input>
            </el-form-item>
            <el-form-item label="性别" porp="sex">
                <el-radio label="男" v-model="form.sex"></el-radio>
                <el-radio label="女" v-model="form.sex"></el-radio>
            </el-form-item>
            <el-form-item label="年龄" porp="age">
                <el-input v-model="form.age" placeholder="Age" clearable="" style="width: 500px">
                    <i slot="prefix" class="el-input__icon el-icon-user"></i>
                </el-input>
            </el-form-item>
            <el-form-item label="班级" porp="classes">
                <el-select v-model="form.classes" placeholder="请选择" style="width: 500px">
                    <el-option
                            v-for="item in classes"
                            :label="item.cname"
                            :key="item.cid"
                            :value="item.cname"
                    >
                    </el-option>
                </el-select>
            </el-form-item>
            <el-form-item label="num" porp="num">
                <el-input v-model="form.num" placeholder="Num" clearable="" style="width: 500px">
                    <i slot="prefix" class="el-input__icon el-icon-user"></i>
                </el-input>
            </el-form-item>
            <el-form-item label="电话" porp="tell">
                <el-input v-model="form.tell" placeholder="Tell" clearable="" style="width: 500px">
                    <i slot="prefix" class="el-input__icon el-icon-user"></i>
                </el-input>
            </el-form-item>
            <el-form-item label="密码" porp="password">
                <el-input v-model="form.password" placeholder="Password" clearable="" style="width: 500px">
                    <i slot="prefix" class="el-input__icon el-icon-user"></i>
                </el-input>
            </el-form-item>
            <el-form-item>
                <el-button  @click="submitForm('form')">提交</el-button>
            </el-form-item>
        </el-form>
    </div>
   <!-- <div>
        <el-table :data="students">
            <el-table-column ></el-table-column>
            <el-table-column ></el-table-column>
                <template slot-scope="scope">
                  <router-link :to="{name:'studentedit'},params:{id:scop.row.id}" tag="el-button">编辑</router-link>
                    <el-button @click="deleteStudent(scope.row.id)">删除</el-button>
                </template>
        </el-table>
    </div>-->
</template>

<script>
    // import student from '../../data/student';
    export default {
        name: "edit",
        data: function () {
            return {
                form: {
                    id: '',
                    username: '',
                    sex: '',
                    age: '',
                    classes: '',
                    num: '',
                    tell: '',
                    password: ''
                },
                classes: [
                    {cid: 1, cname: 'wuif1907-2'},
                    {cid: 2, cname: 'wuif1907-1'},
                    {cid: 3, cname: 'wuif1908'},
                ],
                id:0

            }
        },
        methods:{
            submitForm(){

            },
            getStudent(){
                let form=localStorage.getItem('form');
                if(form){
                    this.form=JSON.parse(form);
                }else{
                    this.$message.error('数据获取失败')
                }
            }
        },
        beforeMount() {
            this.id=this.$route.params.id;
            this.getStudent();
        },
        beforeRouteLeave(){

        }
    }
</script>

<style scoped>

</style>