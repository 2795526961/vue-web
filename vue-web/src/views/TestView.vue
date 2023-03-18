<template>
    <div>
            123321
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

import $http from '../request/index'

export default defineComponent({
    setup () {
        $http.get('/GetUserList')
        return {}
    }
})
</script>

<style scoped>

</style>