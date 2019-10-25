<template>
    <div  id="container">
        <el-form :model="form" id="box" :rules="rules" ref="form">
            <el-form-item label="用户名" prop="username">
                <el-input type="text" v-model="form.username" clearable prefix-icon="el-icon-user" placeholder="username"></el-input>
            </el-form-item>
            <el-form-item label="密码" prop="password">
                <el-input show-password v-model="form.password" clearable prefix-icon="el-icon-lock" placeholder="username">

                </el-input>
            </el-form-item>
            <el-form-item label="角色" prop="role">
                <el-radio v-for="(item,index) in roles" :key="index" v-model="form.role" :label="item"></el-radio>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="handleSubmit('form')">立即创建</el-button>
            </el-form-item>
        </el-form>
    </div>
</template>

<script>
    import admin from '../data/admin';
    import student from '../data/student';
    import teacher from '../data/teacher';

    export default {
        name: "login",
        data: function () {
            return {
                form: {
                    username: '',
                    password: '',
                    role: ''
                },
                roles: ['student', 'teacher', 'admin'],
                rules: {
                    username: [
                        {
                            required: true,
                            message: '用户名必填',
                            trigger: 'blur'
                        }, {
                            min: 2, max: 10, message: '请输入2-10个字符',
                            trigger: 'blur'
                        }
                    ],
                    password: [
                        {
                            required: true,
                            message: '密码必填',
                            trigger: 'blur'
                        },
                        {
                            min: 1, max: 8, message: '请输入1-8位正确密码',
                            trigger: 'blur'
                        }
                    ],
                    role: [
                        {required:true,message:'请选择角色',trigger:'change'}
                    ]
                }
            }
        },
        methods: {
            handleSubmit() {
                // 1.箭头 2.this存储临时变量
                this.$refs.form.validate(valid => {
                    if (valid) {
                        let role = this.form.role;
                        console.log(role);
                        let model = null;
                        if (role == 'admin') {
                            model = admin
                        } else if (role == 'student') {
                            model = student
                        } else {
                            model = teacher
                        }
                        let flag = model.filter(ele => ele.username == this.form.username && ele.password == this.form.password);
                        if (flag.length) {
                            localStorage.user=JSON.stringify(flag[0]);
                            if(role=='student'){
                                this.$router.push({path: 'student'})
                            }else {
                                this.$router.push({path: 'indexs'})  // 1.router link转换为a标签跳转  2.编程式导航跳转
                            }
                        } else {
                            this.$message.warning('用户名密码不匹配')
                        }
                    }
                })
            }
        }
    }
</script>
<style>
    html, body {
        width: 100%;
        height: 100%;
    }
</style>
<style scoped>
    #container {
        position: absolute;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        background-image: url("../assets/2.jpg");
        background-repeat: no-repeat;
        background-size: 100% 100%;
        background-position: center;
    }

    #box {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        width: 340px;
        height: auto;
        border: 1px solid #00ff;
        padding: 10px;
        background-color: rgba(255, 255, 255, 0.5);
        border-radius: 5px;
        box-shadow: 0 0 10px 0 rgba(0, 1, 2, 0.5);
    }
</style>