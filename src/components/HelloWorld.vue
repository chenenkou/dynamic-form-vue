<template>
    <el-container>
        <el-header>
            <el-row>
                <el-col :span="8" :offset="8">
                    <h1>动态表单</h1>
                </el-col>
            </el-row>
        </el-header>
        <el-main>
            <el-row>
                <el-col :span="8" :offset="8">
                    <div>
                        <i-form :config="fields" :model="form" labelWidth="auto" label-suffix=":">
                            <el-row type="flex" justify="center">
                                <el-button @click="onSubmit" type="primary">提交</el-button>
                            </el-row>
                        </i-form>
                    </div>
                </el-col>
            </el-row>

            <el-row>
                <el-col :span="8" :offset="8">
                  <a-component v-model="form.name" @abc="(a) => {console.log(a)}"></a-component>
                </el-col>
            </el-row>
        </el-main>
    </el-container>

</template>

<script>
    import AComponent from "@/components/AComponent";
    export default {
        name: 'HelloWorld',
        props: {
            msg: String
        },
        components: {
            AComponent
        },
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
                    name: '名称',
                    region: '',
                    date: '',
                    delivery: false,
                    type: [],
                    resource: '',
                    desc: ''
                }
            }
        },
        methods: {
            onSubmit() {
                console.log('submit!', this.form);
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
