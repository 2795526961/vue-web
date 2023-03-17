<template>
    <el-form ref="ruleFormRef" :model="ruleForm" status-icon :rules="rules" label-width="120px" class="demo-ruleForm">
        
        <el-form-item label="账号：" prop="userName">
            <el-input v-model="ruleForm.userName" type="userName" autocomplete="off" />
        </el-form-item>

        <el-form-item label="密码：" prop="passWord">
            <el-input v-model="ruleForm.passWord" type="passWord" autocomplete="off" />
        </el-form-item>

        <el-form-item>
      <el-button class="loginbtn" type="primary" @click="submitbtn"
        >登录</el-button
      >
      <el-button class="resetbtn" @click="resetbtn">重置</el-button>
    </el-form-item>

    </el-form>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs } from 'vue'

export default defineComponent({
    setup() {
        const data = reactive({
            ruleForm: {
                userName: "",
                passWord: ""
            },
            rules: {
                userName: [
                    { required: true, message: '不能空', trigger: 'blur' },
                    { min: 3, max: 5, message: '长度必须3 to 5', trigger: 'blur' },
                ],
                passWord: [
                    {
                        required: true,
                        message: '不能空',
                        trigger: 'change',
                    },
                ],
            }

        })


        return { ...toRefs(data) }
    }

    
})

let submitbtn=()=>{
    console.log(123);
    
}

</script>

<style scoped>
.demo-ruleForm{
width: 500px;
margin: 200px auto;

}

</style>