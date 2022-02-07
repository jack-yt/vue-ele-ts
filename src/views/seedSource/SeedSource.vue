<template>
   <el-card class="box-card">
    <el-radio-group v-model="source" @click="changeRadio" size="medium">
      <el-radio-button label="今日头条"></el-radio-button>
      <el-radio-button label="快 手"></el-radio-button>
    </el-radio-group>
    <div class="searchRow">
      <span>人群名称/ID:
        <el-input v-model="message" placeholder="请输入" class="inputStyle" /></span>
      <el-button type="primary" round @click="searchData" style="width: 80px;margin-left:10px;">查询</el-button>
    </div>
    <el-button type="primary" round @click="showWinow" style="width:120px;">
      <i class="el-icon-plus"></i>新建人群
    </el-button>
    <el-table :data="tableData" border style="width: 100%" class="tableStyle">
      <el-table-column prop="name" label="人群名称" />
      <el-table-column prop="id" label="人群ID" />
      <el-table-column prop="number" label="全部覆盖人数" />
      <el-table-column prop="status" label="人群状态" />
      <el-table-column label="操作" width="120">
        <template #default>
          <el-button type="text" @click="clickPush">推送</el-button>
        </template>
      </el-table-column>
    </el-table>
    <el-dialog v-model="isShow" title="添加推送人群" center width="25vw">
      <el-form label-position="right" label-width="100px" :model="formLabelAlign">
        <el-form-item label="应用名称" prop="appName" :rules="[{
          required: true,
          message: '请选择应用，应用不能为空！',
          trigger: 'change',
        }]">
          <el-select v-model="formLabelAlign.appName" placeholder="Activity zone" style="width:100%;">
            <el-option label="Zone one" value="shanghai"></el-option>
            <el-option label="Zone two" value="beijing"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="投放账户" prop="name" :rules="[{
          required: true,
          message: '请输入投放账户，投放账户不能为空！',
          trigger: 'blur',
        }]">
          <el-input v-model.trim="formLabelAlign.name"></el-input>
        </el-form-item>
        <el-form-item label="obs_id" prop="region" :rules="[{
          required: true,
          message: '请输入obs_id，obs_id不能为空！',
          trigger: 'blur',
        }]">
          <el-input v-model.trim="formLabelAlign.region"></el-input>
        </el-form-item>
        <el-form-item label="种子包名称" prop="type" :rules="[{
          required: true,
          message: '请输入种子包名称，种子包名称不能为空！',
          trigger: 'blur',
        }]">
          <el-input v-model.trim="formLabelAlign.type"></el-input>
        </el-form-item>
      </el-form>
      <template #footer>
        <span class="dialog-footer">
          <el-button @click="isShow = false">取消</el-button>
          <el-button type="primary" @click="clickBuild">确定</el-button>
        </span>
      </template>
    </el-dialog>
  </el-card>
</template>

<script setup lang="ts">
  import {
    reactive,
    ref
  } from 'vue';
  let source = ref<string>('今日头条')
  let message = ref<string>('')
  let isShow = ref<boolean>(false)
  let formLabelAlign = reactive({
    appName:'',
    name:'',
    region:'',
    type:''
  })
  let tableData = reactive([])

  function changeRadio() {
    console.log(source.value)
  }

  function searchData() {

  }

  function clickPush() {

  }

  function showWinow() {
    isShow.value = true
  }

  function clickBuild() {
    isShow.value = false;
    console.log(formLabelAlign)
  }

</script>
<style scoped lang="scss">
  .box-card {
    background-color: white;
    padding: 15px;
  }

  .searchRow {
    line-height: 40px;
    font-size: 16px;
  }

  .inputStyle {
    display: inline-block;
    width: 240px;
    margin: 15px;
    height: 40px;
  }

  .tableStyle {
    margin-top: 20px;
  }

</style>
<style>
  .el-dialog--center .el-dialog__footer {
    text-align: right;
  }

</style>
