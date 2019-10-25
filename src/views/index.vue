<template><!--模板-->
    <div id="index">
        <my-nav @insert="insertList"></my-nav>
        <my-button :list="todolist" scene="danger" @indexdelete="indexdelete">

        </my-button>
    </div>
</template>

<script>
    import MyNav from '../components/my-nav';
    import MyButton from '../components/my-button';

    export default {
        name: "index",
        data: function () {
            return {
                todolist: [
                    {id: 1, content: '开题报告、任务书-----下周一', status: false},
                    {id: 2, content: '简历-----下周四', status: false},
                    {id: 3, content: '协同上交开发计划-----下周一', status: false},
                    {id: 4, content: '评审-----下周六', status: false},
                    {id: 5, content: '过程化项目', status: true},
                ],
                content: '',
            }
        },
        methods: {
            insertList(value) {
                let obj = {};
                obj.id = this.todolist[this.todolist.length - 1].id + 1;
                // obj.content = this.content;
                obj.content = value;
                this.stats = false;
                this.todolist.push(obj)
            },
            indexdelete(id) {
                let index = this.todolist.findIndex(ele => ele.id == id);
                this.todolist.splice(index, 1);
            },
            saveList() {
                localStorage.todolist = JSON.stringify(this.todolist);
            },
        },
        watch: {
            todolist: {
                handler: function () {
                    this.saveList();
                },
                deep: true
            },
            content() {

            }
        },
        components: {
            MyNav, MyButton
        }
    }
</script>
<style scoped>
    @import url("https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css");

    .panel {
        width: 300px;
        height: auto;
        border: 1px solid #000;
    }

    ul {
        list-style: none;
    }
</style>