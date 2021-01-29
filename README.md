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
<i-form :config="fields" :model="form" labelWidth="auto" label-suffix=":">
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
                    label: '活动名称',
                    elTag: 'el-input',
                    elAttrs: {}
                },
                region: {
                    label: '活动区域',
                    elTag: 'el-select',
                    elAttrs: {
                        placeholder: '请选择活动区域',
                    },
                    options: [
                        {label: '区域一', value: 'shanghai'},
                        {label: '区域二', value: 'beijing'},
                    ],
                },
                date: {
                    label: '活动日期',
                    elTag: 'el-date-picker',
                    elAttrs: {
                        placeholder: '选择日期',
                    },
                },
                delivery: {
                    label: '即时配送',
                    elTag: 'el-switch',
                    elAttrs: {},
                },
                type: {
                    label: '活动性质',
                    elTag: 'el-checkbox-group',
                    elAttrs: {},
                    options: [
                        {label: '美食/餐厅线上活动', value: 1},
                        {label: '地推活动', value: 2},
                        {label: '线下主题活动', value: 3},
                        {label: '单纯品牌曝光', value: 4},
                    ],
                },
                resource: {
                    label: '特殊资源',
                    elTag: 'el-radio-group',
                    elAttrs: {},
                    options: [
                        {label: '线上品牌商赞助', value: 11},
                        {label: '线下场地免费', value: 12},
                    ],
                },
                desc: {
                    label: '活动形式',
                    elTag: 'el-input',
                    elAttrs: {
                        type: "textarea"
                    }
                }
            },
            form: {
                name: '',
                region: '',
                date: '',
                delivery: false,
                type: [],
                resource: '',
                desc: ''
            }
        }
    }
}
```
