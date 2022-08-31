<template>
  <div>
    <div class="tagBox">
      <el-tag
        v-for="(tag, index) in selectionData"
        class="tagItem"
        :key="index"
        closable
        :disable-transitions="false"
        @close="handleCloseTag(tag)"
      >
        {{ tag.date }} - {{ tag.name }}
      </el-tag>
    </div>
    <el-table
      border
      size="small"
      ref="mutipleTable"
      :data="partData"
      :row-key="getRowKeys"
      @select="handleSelectionChange"
    >
      <el-table-column type="selection" :reserve-selection="true" width="55" />
      <el-table-column property="date" label="零件号"></el-table-column>
      <el-table-column property="name" label="零件名称"></el-table-column>
    </el-table>
  </div>
</template>
<script>
export default {
  data() {
    return {
      selectionData: [],
      partData: [
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1517 弄",
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1519 弄",
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1516 弄",
        },
      ],
    };
  },
  methods: {
    // 统计table选中
    handleSelectionChange(selection) {
      let stockSelectlist = [];
      selection.forEach((el) => {
        stockSelectlist.push(el);
      });
      this.selectionData = stockSelectlist;
    },
    // 删除table选中
    handleCloseTag(tag) {
      this.removeByValue(this.selectionData, "itemBizId", tag.itemBizId);
      this.$nextTick(() => {
        this.$refs.mutipleTable.toggleRowSelection(tag);
      });
    },
    removeByValue(arr, code, value) {
      var index = 0;
      for (var i in arr) {
        if (arr[i][code] === value) {
          index = i;
          break;
        }
      }
      arr.splice(index, 1);
    },
  },
};
</script>
