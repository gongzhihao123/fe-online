<script setup lang="ts">
import {ref} from "vue";
import OrgTree from "./components/OrgTree.vue";
import UserTable from "./components/UserTable.vue";
import { debounce } from "lodash-es"

const selectOrg = ref(0)

const changeTree = debounce((data: any) => {
  selectOrg.value = data.id;
}, 500);

</script>

<template>
  <div>
    <el-row :gutter="20">
      <!-- 左侧tree -->
      <el-col :span="4" :xs="24">
        <OrgTree @node-click="changeTree"/>
      </el-col>
      <!-- 右侧table -->
      <el-col :span="20" :xs="24">
        <UserTable :selectOrg="selectOrg"/>
      </el-col>
    </el-row>
  </div>
</template>

<style scoped></style>