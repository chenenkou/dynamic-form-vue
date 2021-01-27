# dynamic-form-vue

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn run serve
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

## i-form

用法：

1. 定义表单数据模型 model
2. 配置表单项 field ，定义布局（可选）

```html
<i-form :config="fields" :model="model" labelWidth="auto" label-suffix=":">
  <el-row type="flex" justify="center">
    <el-button @click="submit" type="primary">提交</el-button>
    <el-button @click="reset" type="warning" style="margin-left:10px;">重置</el-button>
  </el-row>
</i-form>
```

```js
export default {
  data() {
    return {
      fields: {
        name: {
          label: '用户名',
          elTag: 'el-input',
          elAttrs: {
            placeholder: '请输入用户名'
          },
          customRender: 'nameCheck',
          rules: [{ required: true, message: '用户名不能为空', trigger: 'change' }]
        },
        password: {
          label: '密码',
          elTag: 'el-input',
          elAttrs: {
            type: 'password',
            showPassword: true
          },
          rules: [{ required: true, trigger: 'change' }]
        }
      },
      model: {
        name: '',
        password: ''
      }
    }
  }
}
```

### **IForm Attributes**

| 参数       | 说明                            | 类型    | 可选值 | 默认值 |
| ---------- | ------------------------------- | ------- | ------ | ------ |
| config     | [表单项配置](#IForm.config)  | Object  |        |        |
| model      | 表单数据模型                    | Object  |        |        |
| layout     | [表单布局](#IForm.layout)    | Arrray  |        |        |
| disabled   | 表单整体禁用                    | Boolean |        | false  |
| ...elProps | [表单项配置](#IForm.elProps) | Object  |        |        |

#### **IForm.config**

| 参数               | 说明                                                                                           | 类型                             | 可选值                                                        | 默认值                  |
| ------------------ | ---------------------------------------------------------------------------------------------- | -------------------------------- | ------------------------------------------------------------- | ----------------------- |
| field              | [表单项字段，与 model 属性对](#IForm.field.elAttrs)应                                       | Object                           |
| field.label        | 名称                                                                                           | String                           |
| field.elTag        | element 表单标签                                                                               | String                           | el-input/select/radio/cascader/date-picker/time-picker/upload |
| field.elAttrs      | 表单项属性（参考 elTag 对应组件）                                                              | Object                           |
| field.elStyle      | 表单项 style 样式                                                                              | Object                           |
| field.extra        | 提示信息                                                                                       | String                           |
| field.extraIcon    | 提示信息 icon 图标                                                                             | String                           |                                                               | el-icon-warning-outline |
| field.rules        | [表单校验规则](https://element.eleme.cn/2.0/#/zh-CN/component/form#zi-ding-yi-xiao-yan-gui-ze) | Array                            |
| field.options      | 当为 check，select 作为数据展示                                                                | Array                            |
| field.visible      | 联动，可根据 model[filed] 来控制 **显示隐藏**                                                  | Boolean/String/Function({model}) |
| field.customRender | 展示于 elTag 右侧的模板                                                                        | String                           |
| field.slotRender   | elTag 内部的模板（比如：upload 中的内容）                                                      | String                           |

更多详见：[el-form-item methods](https://element.eleme.cn/2.0/#/zh-CN/component/form#form-item-attributes)

#### **IForm.field.elAttrs**

示例一些特殊属性

| 参数         | 说明                            | 类型                                        | 可选值 | 默认值 |
| ------------ | ------------------------------- | ------------------------------------------- | ------ | ------ |
| disabled     | 禁用                            | Function({model})/ Boolean                  |
| isRemote     | elTag 为 el-select 的延迟加载   | Boolean                                     |        |
| remoteMethod | elTag 为 el-select 的延迟加载   | Function(done,{model}) / Boolean            |
| lazy         | elTag 为 el-cascader 的延迟加载 | Boolean                                     |        |
| lazyLoad     | elTag 为 el-cascader 的延迟加载 | Function(node, resolve, { done }) / Boolean |

#### **IForm.layout**

| 参数     | 说明                              | 类型           | 可选值     | 默认值 |
| -------- | --------------------------------- | -------------- | ---------- | ------ |
| elTag    | element 表单标签                  | String         | el-row/col |
| elAttrs  | 表单项属性（参考 elTag 对应组件） | Object         |            |
| children | 子项                              | Object<layout> |            |
| field    | 表单项字段                        | String         |            |

#### **IForm.elProps**

| 参数         | 说明             | 类型   | 可选值                | 默认值 |
| ------------ | ---------------- | ------ | --------------------- | ------ |
| label-width  | 表单域标签的宽度 | String |                       |        |
| label-suffix | 表单域标签的后缀 | String |                       |        |
| size         | 尺寸             | String | medium / small / mini |        |

更多详见：[el-form attributes](https://element.eleme.cn/2.0/#/zh-CN/component/form#form-attributes)

### **IForm Methods**

| 参数          | 说明         | 类型                             | 可选值 | 默认值 |
| ------------- | ------------ | -------------------------------- | ------ | ------ |
| validate      | 表单数据校验 | Function(err,model)              |
| resetFields   | 重置表单项   | Function(props<Array \| String>) |
| clearValidate | 校验结果清空 | Function(props<Array \| String>) |

更多详见：[el-form methods](https://element.eleme.cn/2.0/#/zh-CN/component/form#form-methods)

## 初始代码引用
详见：[elsa](https://github.com/eminoda/elsa)
