<template>
  <div class="scroll-y">
    <div class="dashboard-container">
      <div class="dashboard-text">name: {{ username }}</div>
    </div>
    <div>update element-plus to 1.2.+, add svg icon, icon-font is abandoned</div>
    <i class="el-icon-add-location">abandoned</i>
    <div>update element-plus version to 1.3.0-beta.7 the size options change to "large default small"</div>
    <div>
      <el-icon>
        <Svg.Edit></Svg.Edit>
      </el-icon>
    </div>
    <div class="mt-2">this is var from vite.config.js define</div>
    <div>{{ showObj }},{{ showObjString }}</div>
  </div>
</template>

<script setup lang="ts">
import * as Svg from '@element-plus/icons-vue'
import { computed, ref } from 'vue'
import { useStore } from 'vuex'

const store = useStore()
const username = computed(() => {
  return store.state.user.username
})

const showObj = ref(GLOBAL_VAR)
// eslint-disable-next-line no-undef
const showObjString = ref(GLOBAL_STRING)
</script>

<style lang="scss" scoped>
.dashboard {
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
</style>
