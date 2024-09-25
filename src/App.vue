<script setup lang="ts">
import { ElButton } from 'element-plus'
import firstDialog from '@/dialogs/first-dialog.vue'
import scendDialog from '@/dialogs/scend-dialog.vue'
import { useDialog } from '@/hooks'
const firstdialog = useDialog(firstDialog)
const scenddialog = useDialog(scendDialog)
const handleOpenDialog = (type: number) => {
  const dialog = type === 1 ? firstdialog : scenddialog
  // 打开弹窗
  dialog({
    // 传入一些myDialog 需要的 props
    title: '弹窗标题',
    onConfirm: () => {
      // 弹窗的回调处理，如果有的话
    },
    onClose: () => {
      // close 回调 ， 如果需要的话
    }
  })
}
</script>

<template>
  <div>
    <ElButton @click="handleOpenDialog(1)"> 打开弹窗1 </ElButton>
    <ElButton @click="handleOpenDialog(2)"> 打开弹窗2 </ElButton>
  </div>
</template>
