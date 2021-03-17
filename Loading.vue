<template>
  这是loading的示范页面：
</template>

<script lang="ts">
import {
  defineComponent,
  onBeforeMount,
  onMounted,
} from "vue";

import { loading } from "ive-vue";
// import { loading } from "@/components";
export default defineComponent({
  setup() {

    onBeforeMount(() => {});
    onMounted(() => {
      const loadingInstance = loading({text:'加载中'});
      setTimeout(() => {
        // 关闭当前实例
        loadingInstance.close();
      }, 2000);
      setTimeout(() => {
        loading('再次加载');
        setTimeout(() => {
          // 清除所有
          loading.clear();
        }, 2000);
      }, 4000);
    });
    return {

    };
  },

});
</script>

<style lang="scss" scoped>

</style>

