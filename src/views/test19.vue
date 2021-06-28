<template>
  <div>
    <div class="block">
      <span class="demonstration">默认</span>
      <el-date-picker v-model="value1" type="date" placeholder="选择日期">
      </el-date-picker>
    </div>
    <div class="block">
      <span class="demonstration">带快捷选项</span>
      <el-date-picker
        v-model="value2"
        align="right"
        type="date"
        placeholder="选择日期"
        :picker-options="pickerOptions"
      >
      </el-date-picker>
    </div>
    <div>
      <!-- {{ pickerOptions }} -->
      <br />
      {{ value1 }}
      <br />
      {{ value2 }}
    </div>
    <div class="block">
      <span class="demonstration">使用 value-format</span>
      <div class="demonstration">值：{{ value3 }}</div>
      <el-date-picker
        v-model="value3"
        type="date"
        placeholder="选择日期"
        format="yyyy 年 MM 月 dd 日"
        value-format="yyyy-MM-dd HH-mm-ss"
      >
      </el-date-picker>
    </div>
    <br />
    <div class="block">
      <p>组件值：{{ value }}</p>
      <el-date-picker
        v-model="value"
        type="daterange"
        start-placeholder="开始日期"
        end-placeholder="结束日期"
        :default-time="['00:00:00', '23:59:59']"
        value-format="yyyy-MM-dd HH-mm-ss"
      >
      </el-date-picker>
    </div>
    <br />
    <div>
      <el-date-picker v-model="value4" type="daterange"> </el-date-picker>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pickerOptions: {
        disabledDate(time) {
          return time.getTime() > Date.now();
        },
        shortcuts: [
          {
            text: "今天",
            onClick(picker) {
              picker.$emit("pick", new Date());
            },
          },
          {
            text: "昨天",
            onClick(picker) {
              const date = new Date();
              date.setTime(date.getTime() - 3600 * 1000 * 24);
              picker.$emit("pick", date);
            },
          },
          // {
          //   text: "一周前",
          //   onClick(picker) {
          //     const date = new Date();
          //     date.setTime(date.getTime() - 3600 * 1000 * 24 * 7);
          //     picker.$emit("pick", date);
          //   },
          // },
        ],
      },
      value1: "",
      value2: "",
      value3: "",
      value: "",
      value4: "",
    };
  },
};
</script>