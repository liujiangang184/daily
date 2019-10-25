<template>
    <div class="box">
        <el-breadcrumb separator="/" style="margin-bottom: 10px">
            <el-breadcrumb-item :to="{path: '/'}">首页</el-breadcrumb-item>
            <el-breadcrumb-item><a href="#">添加学生</a></el-breadcrumb-item>
        </el-breadcrumb>
        <el-form label-width="80px" :model="form"  ref="form"  :rules="rules">
            <el-form-item label="姓名" prop="username">
                <el-input v-model="form.username" placeholder="Username" clearable="" style="width: 500px">
                    <i slot="prefix" class="el-input__icon el-icon-user"></i>
                </el-input>
            </el-form-item>
            <el-form-item label="性别" prop="sex">
                <el-radio label="男" v-model="form.sex"></el-radio>
                <el-radio label="女" v-model="form.sex"></el-radio>
            </el-form-item>
            <el-form-item label="年龄" prop="age">
                <el-input v-model="form.age" placeholder="Age" clearable="" style="width: 500px">
                    <i slot="prefix" class="el-input__icon el-icon-user"></i>
                </el-input>
            </el-form-item>
            <el-form-item label="班级" prop="classes">
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
            <el-form-item label="num" prop="num">
                <el-input v-model="form.num" placeholder="Num" clearable="" style="width: 500px">
                    <i slot="prefix" class="el-input__icon el-icon-user"></i>
                </el-input>
            </el-form-item>
            <el-form-item label="电话" prop="tell">
                <el-input v-model="form.tell" placeholder="Tell" clearable="" style="width: 500px">
                    <i slot="prefix" class="el-input__icon el-icon-user"></i>
                </el-input>
            </el-form-item>
            <el-form-item label="密码" prop="password">
                <el-input v-model="form.password" placeholder="Password" clearable style="width: 500px">
                    <i slot="prefix" class="el-input__icon el-icon-user"></i>
                </el-input>
            </el-form-item>
            <el-form-item>
                <el-button @click="submitForm('form')">提交</el-button>
            </el-form-item>
        </el-form>
    </div>
</template>

<script>
    export default {
        name: "add",
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
                id: 0,
                rules: {
                    username: [{required: true, message: '请输入用户名', trigger: 'blur'}],
                    sex: [{required: true, message: '请选择你的性别', trigger: 'change'}],
                    age: [{require: true, message: '请输入年龄', trigger: 'blur'}],
                    classes: [{require: true, message: '请选择班级', trigger: 'change'}],
                    num: [{required: true, message: '请输入学号', trigger: 'blur'}],
                    tell: [{required: true, message: '请输入电话号码', trigger: 'blur'}],
                    password: [{required: true, message: '请输入密码', trigger: 'blur'}]
                },
            }
        },
        methods: {
            submitForm(form) {
                this.$refs[form].validate((valid) => {
                    if (valid) {
                        this.form.id = Date.now();
                        let form = this.form;
                        localStorage.form = JSON.stringify(form);
                        alert('添加成功')
                    } else {
                        return false;
                    }
                })
            }
        }
    }
</script>

<style scoped>
    el-form {
        width: 500px;
    }
</style>