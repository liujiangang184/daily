<template>
    <div>
        <el-row>
            <el-col :span="6">
                <div class="grid-content bg-purple">
                <ve-line :data="lineData" ></ve-line>
            </div></el-col>
            <el-col :span="6">
                <div class="grid-content bg-purple">
                <ve-line :data="lineData1" ></ve-line>
            </div></el-col>
            <ve-histogram :data="chartData"></ve-histogram>
        </el-row>

    </div>
</template>

<script>
    export default {
        name: "vcharts",
        data(){
            this.lineSettings = {
                labelMap:{
                    'number':'每日提交量'
                }
            }
            return{
                lineData:{
                    columns:['date','number'],
                    rows:[
                        {date:'2019-10-21',number:'41'},
                        {date:'2019-10-22',number:'42'},
                        {date:'2019-10-23',number:'49'},
                        {date:'2019-10-24',number:'45'},
                        {date:'2019-10-25',number:'44'},
                        {date:'2019-10-26',number:'46'},
                        {date:'2019-10-27',number:'47'},
                    ]
                },
                lineData1:{
                    columns:['date','status','skill'],
                    rows:[
                        {date:'7.22',status:100,skill:0},
                        {date:'8.22',status:90,skill:20},
                        {date:'9.22',status:50,skill:50},
                        {date:'10.22',status:80,skill:70},
                        {date:'11.22',status:100,skill:0},
                        {date:'12.22',status:70,skill:90},
                    ]
                },
                chartData: {
                    columns: ['日期', '访问用户', '下单用户', '下单率'],
                    rows: [
                        { '日期': '1/1', '访问用户': 1393, '下单用户': 1093, '下单率': 0.32 },
                        { '日期': '1/2', '访问用户': 3530, '下单用户': 3230, '下单率': 0.26 },
                        { '日期': '1/3', '访问用户': 2923, '下单用户': 2623, '下单率': 0.76 },
                        { '日期': '1/4', '访问用户': 1723, '下单用户': 1423, '下单率': 0.49 },
                        { '日期': '1/5', '访问用户': 3792, '下单用户': 3492, '下单率': 0.323 },
                        { '日期': '1/6', '访问用户': 4593, '下单用户': 4293, '下单率': 0.78 }
                    ]
                }
            }
        }
    }
</script>

<style scoped>

</style>