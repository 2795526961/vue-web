<template>
    <el-form ref="ruleFormRef" :model="logindata" status-icon :rules="rules" label-width="120px"
        class="demo-ruleForm">

        <el-form-item label="账号：" prop="userName">
            <el-input v-model="logindata.userName" type="userName" autocomplete="off" />
        </el-form-item>

        <el-form-item label="密码：" prop="passWord">
            <el-input v-model="logindata.passWord" type="passWord" autocomplete="off" />
        </el-form-item>

        <el-form-item>
            <el-button class="loginbtn" type="primary" @click="submitbtn">登录</el-button>
        </el-form-item>

    </el-form>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs } from 'vue'
import { ElMessage } from 'element-plus'
import $http from '../request/index'
import  router from '../router/index'
export default defineComponent({
    setup() {
        //登录的model提交数据
        const logindata = reactive({
                userName: "",
                passWord: ""
        })
        //规则
        const rules=reactive({
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
        })
        //登录方法
        let submitbtn = () => {
            if (!logindata.userName || !logindata.passWord) {
                ElMessage.error('空')
                return
            }

        //    let Geturl='/GetUser?'+'username='+logindata.ruleForm.userName
        //     $http.get(Geturl).then(res=>{
        //         console.log(res);
                
        //     })

            let PostUrl='/PostUser'
            var temp={
                "username":logindata.userName,
                "password":logindata.passWord
            }

            $http.post(PostUrl,temp).then(res=>{

                console.log(res);
                //跳转
                router.push('/test')
            })

        }





        return { logindata, submitbtn ,rules}
    }
})



</script>

<style scoped>
.demo-ruleForm {
    width: 500px;
    margin: 200px auto;

}
</style>