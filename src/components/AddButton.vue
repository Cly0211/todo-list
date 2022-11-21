<template>
  <div>
  <el-button class="add-button" type="primary" @click="click">
    <el-icon><CirclePlus /></el-icon>
    ADD
  </el-button>
  </div>
</template>

<script>
export default {
  name: 'AddButton',
  setup(props, { emit }) {
    function click() {
      emit('click');
    }
    return {
      click,
    };
  },
};
</script>

<style>
.add-button {
  color: white;
}
</style>
