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
                        <i-form :config="fields" :model="model" labelWidth="auto" label-suffix=":">
                            <el-row type="flex" justify="center">
                                <el-button @click="onSubmit" type="primary">提交</el-button>
                            </el-row>
                        </i-form>
                    </div>
                </el-col>
            </el-row>
        </el-main>
    </el-container>

</template>

<script>
    export default {
        name: 'HelloWorld',
        props: {
            msg: String
        },
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
        },
        methods: {
            onSubmit() {
                console.log('submit!', this.model);
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
