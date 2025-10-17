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
          <img src="/svg.png" alt="Logo" class="header-logo"/>
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
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08), 0 1px 4px rgba(0, 0, 0, 0.06);
	background: rgba(255, 255, 255, 0.98);
	backdrop-filter: blur(10px);
	-webkit-backdrop-filter: blur(10px);
}

/* 水平导航高度 */
.el-header {
    --el-header-height: 20px;
}

.header-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 64px;
  padding: 0 32px;
  max-width: 1600px;
  margin: 0 auto;
}

.header-left {
  display: flex;
  align-items: center;
}

.header-logo {
  height: 42px;
  width: auto;
  max-width: 100%;
  object-fit: contain;
  transition: transform 0.3s ease, filter 0.3s ease;
}

.header-logo:hover {
  transform: scale(1.05);
  filter: brightness(1.1);
}

.header-right {
  display: flex;
  align-items: center;
  flex: 1;
  justify-content: flex-end;
  margin-left: 24px;
}

.header-title {
  font-size: 22px;
  font-weight: 700;
  color: #1a202c;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  letter-spacing: -0.02em;
  transition: color 0.3s ease;
}

.header-title:hover {
  color: #42b983;
}

/* 响应式设计 */
@media (max-width: 1200px) {
  .header-title {
    font-size: 18px;
  }
}

@media (max-width: 768px) {
  .header-container {
    padding: 0 10px;
  }
  
  .header-logo {
    height: 30px;
  }
  
  .header-title {
    font-size: 14px;
    letter-spacing: 0.5px;
  }
  
  .header-right {
    margin-left: 10px;
  }
}

@media (max-width: 480px) {
  .header-logo {
    height: 25px;
  }
  
  .header-title {
    font-size: 12px;
  }
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