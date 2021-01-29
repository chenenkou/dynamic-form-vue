<script>
    export default {
        components: {},
        props: {
            model: Object,
            fieldOptions: {
                type: Object,
                default() {
                    return {elAttrs: {}}
                }
            },
            value: [Number, String, Array, Date, Boolean],
            field: String,
            disabled: Boolean
        },
        data() {
            return {
                options: []
            }
        },
        computed: {
            elAttrs() {
                return this.fieldOptions.elAttrs || {}
            },
            elStyle() {
                return this.fieldOptions.elStyle || {}
            }
        },
        methods: {
            // 渲染表单元素操作项
            renderOptions(elTag) {
                if (!this.options || !Array.isArray(this.options)) {
                    return null
                }
                const parentElTags = ['el-checkbox-group', 'el-radio-group', 'el-select']
                const optionsTags = ['el-checkbox', 'el-radio', 'el-option']
                if (!parentElTags.includes(elTag)) {
                    return null
                }

                let childElTag = optionsTags[parentElTags.indexOf(elTag)]
                if (!childElTag) {
                    return null
                }
                const children = []
                const valueIsLabel = function () {
                    return ['el-checkbox-group', 'el-radio-group'].includes(elTag)
                }

                this.options.forEach(option => {
                    children.push(
                        this.$createElement(
                            childElTag,
                            {
                                props: {
                                    label: valueIsLabel() ? option.value : option.label,
                                    value: option.value,
                                    disabled: option.disabled
                                }
                            },
                            option.label
                        )
                    )
                })
                return children
            }
        },
        // 渲染表单元素
        render(createElement) {
            const {elTag} = this.fieldOptions

            return createElement(
                elTag,
                {
                    props: {
                        ...this.elAttrs,
                        value: this.value,
                        props: this.elAttrs.props,
                        disabled: this.disabled || false
                    },
                    attrs: {
                        ...this.elAttrs,
                        placeholder: this.elAttrs.placeholder || ''
                    },
                    style: this.elStyle,
                    on: {
                        input: value => {
                            this.$emit('change', value)
                        }
                    }
                },
                [this.renderOptions(elTag)]
            )
        },
        // 模板创建前获取单表单元素的下拉/多选..操作选项数据
        created() {
            const {options} = this.fieldOptions
            if (Array.isArray(options)) {
                this.options = options
            }
        }
    }
</script>

<style scoped>
</style>
