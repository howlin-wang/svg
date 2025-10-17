<script lang="ts" setup>

import { ElIcon } from 'element-plus'
import { HomeFilled, SuccessFilled } from '@element-plus/icons-vue'

// 个人主页
const home = {
    name: "My Blog",
    link: "https://junyaohu.github.io/",
}

// 项目主页
const logo = {
    name: "Template",
    link: "#",
}

// 右侧更多菜单
const more_paper = {
    "ExtDM": {
        name: "ExtDM - CVPR 2024",
        link: "https://zzcheng.top/ExtDM/",
    },
    "MPOT": {
        name: "MPOT - ICCV 2023",
        link: "https://zzcheng.top/MPOT/",
    },
    "ControlNet": {
        name: "ControlNet - ICCV 2023",
        link: "https://github.com/lllyasviel/ControlNet",
    }
}

</script>

<template>
    <!-- 设置页首始终悬浮顶部 -->
    <el-affix :offset="0" :style="{width: '100%'}">
      <div class="header-container">
        <div class="header-left">
          <img src="svg.png" alt="Logo" class="header-logo"/>
        </div>
        <div class="header-right">
          <div class="header-title">Latent Diffusion Model without Variational Autoencoder</div>
        </div>
      </div>
    </el-affix>
</template>

<style>

/* 导航背景 */
.el-menu {
	background: none;
}

/* 下拉菜单宽度 */
.el-menu--popup {
	min-width: 100%;
}

/* 导航背景特效和阴影 */
.el-affix--fixed {
	box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.1);
	background-image: radial-gradient(#ffffffca 1px,#ffffff 1px);
	background-size: 3px 3px;
}

/* 水平导航高度 */
.el-header {
    --el-header-height: 20px;
}

.header-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 60px; /* 与 el-header 高度一致 */
  padding: 0 20px;
}

.header-left {
  display: flex;
  align-items: center;
}

.header-logo {
  height: 40px;
  width: auto;
}

.header-right {
  display: flex;
  align-items: center;
}

.header-title {
  font-size: 22px;
  font-weight: 800;
  color: #222;
  font-family: "MyFont", Verdana, sans-serif;
  letter-spacing: 1px;
}

.el-menu--horizontal {
    --el-menu-horizontal-height: 60px;
}

</style>

<style scoped>

/* 水平导航左右分区 */
.el-menu--horizontal > .el-menu-item:nth-child(2) {
    margin-right: auto;
}

/* 取消鼠标焦点悬浮在链接上的颜色装饰 */
a:hover {
  color: inherit;
  border-bottom: none;
}

/* 链接装饰，取消下划线和链接颜色 */
a {
	text-decoration: None;
	color: inherit;
}

</style>