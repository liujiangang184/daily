<template>
    <div>
        <el-table :data="students">
            <el-table-column prop="id" label="ID"></el-table-column>
            <el-table-column prop="username" label="姓名"></el-table-column>
            <el-table-column
                    fixed="right"
                    label="操作">
                <template slot-scope="scope">
                    <router-link :to="{name:'studentedit',params:{id:scope.row.id}}" tag="el-button">编辑</router-link>
                    <el-button type="danger" @click="deleteStudent(scope.row.id)">
                        删除
                    </el-button>
                </template>
            </el-table-column>
        </el-table>
    </div>
</template>

<script>
    import student from '../../data/student';

    export default {
        name: "query",
        data() {
            return {
                students: []
            }
        },
        methods: {
            getStudent() {
                let students = JSON.parse(localStorage.getItem('form'));
                student.push(students);
                let a = student.slice(0, -1);
                this.students = a;
            },
            deleteStudent(id) {
                // findindex splice
               let student = this.student.filter(ele => ele.id != id);
                this.students.splice(student,1);
                console.log(this.student);
            }
        },
        // 生命周期函数
        mounted() {
            this.getStudent();
        },
    }
</script>

<style scoped>

</style>