<template>
    <div>
        <div style="padding-bottom: 10px">查看日报</div>
        <el-table :data="dailyArr">
            <el-table-column prop="names" label="名字"></el-table-column>
            <el-table-column prop="content" label="内容"></el-table-column>
            <el-table-column prop="finish" label="完成度"></el-table-column>
            <el-table-column prop="motto" label="座右铭"></el-table-column>
            <el-table-column prop="suggest" label="建议"></el-table-column>
            <el-table-column prop="problem" label="问题"></el-table-column>
            <el-table-column prop="feeling" label="心得体会"></el-table-column>
            <el-table-column prop="other" label="其他"></el-table-column>
            <el-table-column prop="ctime" label="创建时间"></el-table-column>
        </el-table>
        <!-- <el-pagination
         layout="total,prev,pager,next,jumper" :total="total"
         page-size="3"
         ></el-pagination>-->
        <my-page :total="total" :page-size="3"
                 @changepage="getDaily"
        ></my-page>
    </div>
</template>

<script>
    import {SUCCESS, FAIL, HOSTNAME} from "../../config/base";
    import MyPage from "../../components/my-page"

    export default {
        name: "query",
        data() {
            return {
                dailyArr: [],
                total: 0,
                user: null,
                limit: 2,

            }

        },
        components: {
            MyPage
        },
        methods: {
            /*  changePage(i){


              },*/
            getDaily(i = 1) {
                let user = this.user.username;
                let qs = '?names=' + user + '&page=' + i + '&limit=' + this.limit;
                fetch(HOSTNAME + 'index/index/query' + qs)
                    .then(res => res.json())
                    .then(data => {
                        if (data.code == SUCCESS) {
                            this.dailyArr = data.data;
                            this.total = data.count;
                            console.log(data);
                        } else if (data.code == FAIL) {
                            console.log(data);
                        }
                    })
            },
            getUser() {
                this.user = JSON.parse(localStorage.user)
            }
        },
        beforeMount() {
            this.getUser();
            this.getDaily();
        }
    }
</script>

<style scoped>

</style>