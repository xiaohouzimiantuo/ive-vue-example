# ive-vue

## Project setup
```
yarn install ive-vue --save
```

### use in html
```
<script src="vue3_path/vue.runtime.global.js"></script>
<script src="your_path/iveVue.umd.js"></script>

<script>
  iveVue.modal({
    title: "自定义模板",
    content: '{{label}}<input v-modal="name">',
    data: { name: "我和content模板中的值关联", label: 'exaxple'},
    footer: [
      {
        type: 'delete',
        text: '取消',
        onClick: (data, close) => {
          console.log(data);
          alert("你取消了");
          close();
        },
      },
      {
        type: 'primary',
        text: '确定',
        onClick: (data, close) => {
          console.log(data);
          if (data.name.length > 18) {
            close();
          } else {
            alert("name的长度小于18");
          }
        },
      },
    ]
  });
</script>

```
### use in es2015
```
import { modal, modalFormTemplate } from 'ive-vue';
modal({
  title: "modalFormTemplate默认模板",
  content: modalFormTemplate,
  data: { name: "name", label: 'modalFormTemplate的label'},
  footer: [
    {
      onClick: (data, close) => {
        console.log(data);
        if (data.name.length > 10) {
          close();
        } else {
          alert("name的长度小于10");
        }
      },
    },
  ]
});
```


```

