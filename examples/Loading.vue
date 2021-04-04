<template>
  这是loading的示范页面：
</template>

<script lang="ts">
import {
  defineComponent,
  onBeforeMount,
  onMounted,
} from "vue";

import { IveLoading } from "ive-vue";
export default defineComponent({
  setup() {
    onBeforeMount(() => {});
    onMounted(() => {
      const loadingInstance = IveLoading.show({text:'加载中'});
      setTimeout(() => {
        // 关闭当前实例
        loadingInstance.close();
      }, 2000);
      setTimeout(() => {
        IveLoading.show('再次加载');
        setTimeout(() => {
          // 清除所有
          IveLoading.clear();
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

