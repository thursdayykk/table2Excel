<template>
    <div>
        <el-button @click="toExcel" type="warning" size="mini" :loading="toExcelLoading">导出</el-button>
        <el-table
            id="table-id-2019"
            :data="tableData"
            style="width: 100%">
            <el-table-column
            prop="date"
            label="日期"
            width="150">
            </el-table-column>
            <el-table-column label="配送信息">
            <el-table-column
                prop="name"
                label="姓名"
                width="120">
            </el-table-column>
            <el-table-column label="地址">
                <el-table-column
                prop="province"
                label="省份"
                width="120">
                </el-table-column>
                <el-table-column
                prop="city"
                label="市区"
                width="120">
                </el-table-column>
                <el-table-column
                prop="address"
                label="地址"
                width="300">
                </el-table-column>
                <el-table-column
                prop="zip"
                label="邮编"
                width="120">
                </el-table-column>
            </el-table-column>
            </el-table-column>
        </el-table>
    </div>
</template>

<script>
const { export_json_to_excel } = require('./utils/Export2Excel')
  export default {
    data() {
      return {
        toExcelLoading:false,
        tableData: [{
          date: '2016-05-03',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }, {
          date: '2016-05-02',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }, {
          date: '2016-05-04',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }, {
          date: '2016-05-01',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }, {
          date: '2016-05-08',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }, {
          date: '2016-05-06',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }, {
          date: '2016-05-07',
          name: '王小虎',
          province: '上海',
          city: '普陀区',
          address: '上海市普陀区金沙江路 1518 弄',
          zip: 200333
        }]
      }
    },
    methods:{
        toExcel(){
            this.toExcelLoading = true
            require.ensure([], _ => {
                const tHeader = ['日期', '姓名', '地址']
                const filterVal = ['date', 'name', 'address']
                const list = this.tableData
                const data = this.formatJson(filterVal, list)
                console.log(data)
                export_json_to_excel(tHeader,data, '列表excel')
                this.$nextTick(()=>{
                    this.toExcelLoading = false
                })
                
            })
        },
        formatJson(filterVal, jsonData) {
            return jsonData.map(v => filterVal.map(j => v[j]))
        }
    }
  }
</script>