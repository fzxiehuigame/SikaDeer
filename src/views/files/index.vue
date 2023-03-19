<template>
  <div>
    Hello World
    <el-dropdown
      split-button
      type="success"
      @command="handleCommand"
    >
      上传文件
      <el-dropdown-menu slot="dropdown">
        <el-dropdown-item command="uploadFile">上传文件</el-dropdown-item>
        <el-dropdown-item command="uploadFiles">上传文件夹</el-dropdown-item>
      </el-dropdown-menu>
    </el-dropdown>
    <el-upload
      drag
      :action="uploadUrl"
      multiple
    >
      <i class="el-icon-upload" />
      <div>可以上传文件夹,但是无法保留目录信息</div>
    </el-upload>
  </div>
</template>

<script>
export default {
  name: 'FilesIndex',
  data() {
    return {
      uploadUrl: window.location.origin + '/api/upload'
    }
  },
  methods: {
    handleCommand(command) {
      if (command === 'uploadFiles') {
        this.$nextTick(() => {
          document.getElementsByClassName(
            'el-upload__input'
          )[0].webkitdirectory = true
        })
      } else {
        this.$nextTick(() => {
          document.getElementsByClassName(
            'el-upload__input'
          )[0].webkitdirectory = false
        })
      }
    }
  }
}
</script>
