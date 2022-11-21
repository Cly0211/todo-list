<template>
  <div>
    <Banner @add="add"></Banner>
    <TaskList
      :tableData="tableData"
      @edit="edit"
      @delete="deleteItem"
    ></TaskList>
    <InputDialog
      ref="dialogRef"
      :tableData="tableData"
      :editInfo="editInfo"
      @handleSubmit="handleSubmit"
      @add="added"
    ></InputDialog>
  </div>
</template>

<script>
import { ref } from 'vue';
import Banner from './components/Banner.vue';
import InputDialog from './components/InputDialog.vue';
import TaskList from './components/TaskList.vue';

export default {
  name: 'App',
  components: {
    Banner,
    TaskList,
    InputDialog,
  },
  setup() {
    let editInfo = ref(null);
    let dialogRef = ref(null);
    const tableData = ref([
      {
        title: 'title1',
        description: 'description1',
        deadline: '11/11/2022',
        priority: 'high',
        completed: false,
      },
      {
        title: 'title2',
        description: 'description2',
        deadline: '11/11/2022',
        priority: 'low',
        completed: false,
      },
    ]);
    let row = ref(null);

    function add() {
      editInfo.value = null;
      dialogRef.value.show = true;
    }
    function edit(row) {
      editInfo.value = row;
      dialogRef.value.show = true;
    }
    const handleSubmit = (val) => {
      console.log('这里拿到数据：', val);
    };

    function deleteItem(row) {
      tableData.value = tableData.value.filter((i) => i !== row);
    }
    function added(row) {
      tableData.value.push(row);
    }

    return {
      add,
      handleSubmit,
      dialogRef,
      editInfo,
      tableData,
      edit,
      deleteItem,
      added,
    };
  },
};
</script>

<style></style>
