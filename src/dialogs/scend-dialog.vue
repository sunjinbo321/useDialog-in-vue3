<script setup lang="ts" name="ScendDialog">
import { computed } from 'vue'
const props = defineProps<{
    visible: boolean
    title?: string
    onConfirm: () => void
}>()

const emits = defineEmits<{
    close: []
    'update:visible': [boolean]
}>()

// 取消选择
const cancel = () => {
    dialogVisible.value = false
}

// 确认选择
const confirm = () => {
    // 其他逻辑
    props?.onConfirm()
    cancel()
}

const dialogVisible = computed<boolean>({
    get() {
        return props.visible
    },
    set(visible) {
        emits('update:visible', visible)
        if (!visible) {
            emits('close')
        }
    }
})
</script>

<template>
    <el-dialog v-model="dialogVisible" :title="props.title" width="800" :before-close="cancel">
        <div>我是弹窗2</div>
        <template #footer>
            <el-button @click="cancel"> 取消 </el-button>
            <el-button type="primary" @click="confirm"> 确定 </el-button>
        </template>
    </el-dialog>
</template>
