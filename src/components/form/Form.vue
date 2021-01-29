<script>
    import FormItem from './FormItem/Index'

    export default {
        name: 'i-form',
        components: {FormItem},
        props: {
            config: Object,
            disabled: Boolean
        },
        computed: {
            elFormOptions() {
                // 包含了父作用域中不作为 props 被识别 (且获取) 的特性绑定 (class 和 style 除外)
                return this.$attrs
            }
        },
        methods: {
            // 渲染单个表单项元素
            renderFormItem(field) {
                const {elTag, changeMethod} = this.config[field]
                if (!elTag) {
                    console.warn(`请设置 config[${field}].elTag`)
                    return ''
                }
                return this.$createElement('form-item', {
                    props: {
                        field,
                        disabled: this.disabled,
                        value: this.elFormOptions.model[field],
                        fieldOptions: this.config[field],
                        model: this.elFormOptions.model
                    },
                    on: {
                        change: value => {
                            this.elFormOptions.model[field] = value
                            if (changeMethod) {
                                changeMethod.bind(this)({
                                    value,
                                    model: this.elFormOptions.model,
                                    field,
                                    rules: this.rules
                                })
                            }
                        }
                    }
                })
            },
            // 渲染单个表单项
            renderElFormItem(field) {
                const {elTag, elAttrs, options, visible, ...elFormItemOptions} = this.config[field]
                // https://element.eleme.io/#/zh-CN/component/form#form-item-attributes
                const props = {...elFormItemOptions, prop: field}
                return this.$createElement('el-form-item', {props}, [this.renderFormItem(field)])
            },
            // 渲染表单所有项布局
            drawLayout() {
                const renders = []
                for (let field in this.elFormOptions.model) {
                    const formItemRender = this.renderElFormItem(field)
                    renders.push(formItemRender)
                }
                return renders
            },
            // 渲染表单提交/取消...按钮
            renderActionBar() {
                if (this.$scopedSlots.default) {
                    return this.$scopedSlots.default()
                }
                return ''
            }
        },
        // 渲染表单
        render(createElement) {
            return createElement(
                'el-form',
                {
                    props: this.elFormOptions,
                    on: this.$listeners,
                    ref: 'elFormRef'
                },
                [...this.drawLayout(), ...this.renderActionBar()]
            )
        }
    }
</script>

<style scoped>
</style>
