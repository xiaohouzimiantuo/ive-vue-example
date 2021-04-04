<template>
  这是imodal的示范页面：
  <br />
  在footer的onClick事件中，从回调取当前v-modal绑定数据的值,
  <br />
  modalFormTemplate 的值为: {{ modalFormTemplate }}
</template>

<script lang="ts">
import { defineComponent, onBeforeMount, onMounted } from "vue";
import { IveModal } from "ive-vue";
export default defineComponent({
  setup() {
    onBeforeMount(() => {});
    onMounted(() => {
      function showTem() {
        IveModal.show({
          title: "modalFormTemplate默认模板",
          content: IveModal.modalFormTemplate,
          data: { name: "name", label: "modalFormTemplate的label" },
          footer: [
            {
              type: "delete",
              text: "取消",
              onClick: (data, close) => {
                console.log(data);
                alert("你取消了");
                close();
              },
            },
            {
              type: "primary",
              text: "确定",
              onClick: (data, close) => {
                console.log(data);
                if (data.name.length > 18) {
                  close();
                } else {
                  alert("name的长度小于18");
                }
              },
            },
          ],
        });
      }
      IveModal.show({
        title: "从回调取当前v-modal绑定数据的值",
        content: `<input v-model="test" class="test" />
        <p>{{test2}}</p>
        <input v-model="test1" class="test" />`,
        data: {
          test: "第一个input的数据",
          test1: "第二个input的数据",
          test2: "通过v-modal绑定input中的数据",
        },
        footer: [
          {
            onClick: (data, close) => {
              console.log(data);
              close();
              showTem();
            },
          },
        ],
      });
    });
    return {
      modalFormTemplate: IveModal.modalFormTemplate,
    };
  },
});
</script>

<style lang="scss" scoped>
</style>

