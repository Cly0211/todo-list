<template>
  <el-table :data="tableData" height="250" style="width: 100%">
    <el-table-column prop="title" label="Title" width="180" />
    <el-table-column prop="description" label="Description" width="180" />
    <el-table-column prop="deadline" label="Deadline" />
    <el-table-column prop="priority" label="Priority" />
    <el-table-column prop="completed" label="Is Complete">
      <template #default="scope">
        <el-checkbox v-model="scope.row.completed" />
      </template>
    </el-table-column>
    <el-table-column prop="action" width="250" label="Action">
      <template #default="scope">
        <el-button
          class="update-button"
          type="primary"
          @click="updateRow(scope.row)"
          v-show="!scope.row.completed"
        >
          <el-icon><Edit /></el-icon>
          Update
        </el-button>
        <el-button
          class="delete-button"
          type="danger"
          @click="deleteRow(scope.row)"
        >
          <el-icon><Remove /></el-icon>
          Delete
        </el-button>
      </template>
    </el-table-column>
  </el-table>
</template>
<script>
export default {
  name: 'TaskList',
  components: {},
  props: {
    tableData: Array,
  },
  data() {
    return {
      // completed:false,
    };
  },
  methods: {
    updateRow(row) {
      //找到这个title的数据把completed改为true
      this.$emit('edit', row);
    },
    deleteRow(row) {
      this.$message({
        message: 'task was deleted successfully',
        type: 'success',
      });
      this.$emit('delete', row);
    },
  },
};
// Vue.component('el-checkbox', {

//   model: {
//     prop: 'completed',
//     event: 'change'
//   },
//   props: {
//     completed: Boolean
//   },

//   template: `
//     <input
//       type="completed"
//       v-bind:completed="completed"
//       v-on:change="$emit('change', $event.target.completed)"
//     >
//   `
// })
</script>
<style>
.task-table {
  color: rgba(0, 0, 0, 0.65);
  font-size: 10px;
  line-height: 1.5;
}
</style>
