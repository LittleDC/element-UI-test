<template>
  <div>
    <div class="block">
      <span class="demonstration">页数较少时的效果</span>
      <el-pagination
        layout=" total,jumper,sizes,prev,pager,next"
        :page-size="20"
        :page-sizes="[10, 20, 30]"
        :total="50"
      >
      </el-pagination>
    </div>
    <div class="block">
      <span class="demonstration">大于 7 页时的效果</span>
      <el-pagination layout="prev, pager, next" :total="1000"> </el-pagination>
    </div>
    <div class="block">
      <span class="demonstration">设置最大页码按钮数</span>
      <el-pagination
        :page-size="20"
        :pager-count="5"
        layout="prev, pager, next"
        :total="1000"
      >
      </el-pagination>
    </div>
    <div class="block">
      <span class="demonstration">带有背景色的分页</span>
      <el-pagination background layout="prev, pager, next" :total="1000">
      </el-pagination>
    </div>
    <div class="block">
      <span class="demonstration">小型分页</span>
      <el-pagination small layout="prev, pager, next" :total="50">
      </el-pagination>
    </div>
    <div class="block">
      <span class="demonstration">当只有一页时隐藏分页</span>
      <div>
        <el-switch v-model="value"> </el-switch>
        <el-pagination
          :hide-on-single-page="value"
          :total="5"
          layout="prev, pager, next"
        >
        </el-pagination>
      </div>
    </div>
    <div class="block">
      <br />
      ------------------------这是一条华丽的分割线 --------------------------
      <br />
      <br />
    </div>
    <div class="block">
      <span class="demonstration">显示总数</span>
      <el-pagination
        @current-change="handleCurrentChange"
        :current-page.sync="currentPage1"
        :page-size="100"
        layout="total, prev, pager, next"
        :total="1000"
      >
      </el-pagination>
    </div>
    <div class="block">
      <span class="demonstration">调整每页显示条数</span>
      <el-pagination
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
        :current-page.sync="currentPage2"
        :page-sizes="[100, 200, 300, 400]"
        :page-size="100"
        layout="sizes, prev, pager, next"
        :total="1000"
      >
      </el-pagination>
    </div>
    <div class="block">
      <span class="demonstration">直接前往</span>
      <el-pagination
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
        :current-page.sync="currentPage3"
        :page-size="100"
        layout="prev, pager, next, jumper"
        :total="1000"
      >
      </el-pagination>
    </div>
    <div class="block">
      <span class="demonstration">完整功能</span>
      <el-pagination
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
        :current-page="currentPage4"
        :page-sizes="[100, 200, 300, 400]"
        :page-size="100"
        layout="total, sizes, prev, pager, next, jumper"
        :total="400"
      >
      </el-pagination>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      value: false,
      currentPage1: 1,
      currentPage2: 5,
      currentPage3: 5,
      currentPage4: 4,
    };
  },
  methods: {
    handleSizeChange(val) {
      console.log(`每页 ${val} 条`);
    },
    handleCurrentChange(val) {
      console.log(`当前页: ${val}`);
    },
  },
};
</script>