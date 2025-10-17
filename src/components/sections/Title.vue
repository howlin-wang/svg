<script lang="ts" setup>

import { ElIcon } from 'element-plus'
import { Document, Files, MagicStick, Picture, DataAnalysis, Film } from '@element-plus/icons-vue'

// logo地址，没有则置为""即可
const logo = './svg.png'

// 标题
const title = 'Latent Diffusion Model without Variational Autoencoder'

// 标题颜色
const title_color = '#000000'

// 标题补充，没有则置为''即可
const title_supp = ''

// 标题补充颜色
const title_supp_color = '#42B883'

// 按钮颜色
const btn_color = '#444444'

// 作者清单（包含作者姓名、头像、主页、地址序号）
const authors = [
  { name: "Minglei Shi", icon: "", homepage: "https://github.com/shiml20", address_flag: "1,#" },
  { name: "Haolin Wang", icon: "", homepage: "https://howlin-wang.github.io/", address_flag: "1,#" },
  { name: "Wenzhao Zheng", icon: "", homepage: "https://wzzheng.net/", address_flag: "1,*" },
  { name: "Ziyang Yuan", icon: "", homepage: "https://scholar.google.ru/citations?user=fWxWEzsAAAAJ&hl=en", address_flag: "2" },
  { name: "Xiaoshi Wu", icon: "", homepage: "https://scholar.google.com/citations?user=cnOAMbUAAAAJ&hl=en", address_flag: "2" },
  { name: "Xintao Wang", icon: "", homepage: "https://xinntao.github.io/", address_flag: "2" },
  { name: "Pengfei Wan", icon: "", homepage: "https://scholar.google.com/citations?user=P6MraaYAAAAJ&hl=en", address_flag: "2" },
  { name: "Jie Zhou", icon: "", homepage: "https://www.imem.tsinghua.edu.cn/info/1330/2128.htm", address_flag: "1" },
  { name: "Jiwen Lu", icon: "", homepage: "https://www.au.tsinghua.edu.cn/info/1078/3156.htm", address_flag: "1" },
]

// 地址清单（包含地址名称、头像、主页、地址序号）
const addresses = [
  {
    address_flag: "1",
    name: "Automation Department, Tsinghua University",
    icon: "",
    homepage: "https://www.au.tsinghua.edu.cn/en/"
  },
  {
    address_flag: "2",
    name: "Kling Team, KuaiShou Technology",
    icon: "",
    homepage: "https://klingai.com/cn/"
  },
]

// 共一和通讯提示
const con_and_corresponding_author = [
  "#: Equal Contribution. Listed in alphabetical order.",
  "*: Project Leader."
]

// 最新消息
// const news = "🔥 [2024-12-15] This template project is still under development."

// 强调内容
const emphases = [
  "🎉 [ABCD 2024] Poster",
  "🥰 欢迎关注“减论”微信公众号/B站/知乎/小红书",
  "传递人工智能算法科普教育的减约理解",
  "提升信息效率及认知维度"
]

// 提供引导资料链接
const buttons = [
  {
    disabled: true,
    name: "Paper",
    component: Document,
  },
  {
    disabled: false,
    name: "Code",
    link: "https://github.com/JunyaoHu/academic-project-page-template-vue",
    component: Files,
  },
]

</script>

<template>
  <div>

    <!-- 最新消息提示 -->
    <!-- <el-row justify="center">
      <el-col :span="24">
        <el-alert title="🔥 This template is still under development." type="success" />
      </el-col>
    </el-row> -->

    <!-- 文章标题 -->
    <el-row justify="center" align="middle" class="title-row">
      <el-col :span="20" class="title-container">
        <div class="title-with-logo">
          <el-image v-if="logo" :src="logo" class="logo-inline" fit="contain" />
          <h1 class="paper-title">
            <span v-if="title" :style="{color:title_color}">{{ title }}</span>
            <span v-if="title_supp" :style="{color:title_supp_color}">{{ title_supp }}</span>
          </h1>
        </div>
      </el-col>
    </el-row>

    <!-- 作者名单 -->
    <el-row justify="center">
      <a :href=author.homepage class="author-link" v-for="author in authors">
        <el-button class="title-button" type="primary" text>
          <span class="author">
            {{ author.name }}<sup v-if="author.address_flag" class="name_sup">{{ author.address_flag }}</sup>
          </span>
        </el-button>
      </a>
    </el-row>

    <!-- 地址名单 -->
    <el-row justify="center">
      <a :href=address.homepage class="address-link" v-for="address in addresses">
        <el-button class="title-button" type="primary" text>
          <span class="address">
            <sup v-if="address.address_flag" class="address_sup">{{ address.address_flag }}</sup>{{ address.name }}
          </span>
        </el-button>
      </a>
    </el-row>

    <!-- 共一和通讯提示内容 -->
    <el-row justify="center" class="con-cor" v-for="line in con_and_corresponding_author">
        {{ line }}
    </el-row>


    <!-- 强调内容 -->
    <!-- <el-row justify="center" class="emphasis" v-for="emphasis in emphases">
        {{ emphasis }}
    </el-row> -->

    <!-- 提供引导按钮 -->
    <el-row justify="center" style="margin-bottom: 20px;">
      <el-col :span="20">
        <el-row justify="center">
          <a :href=button.link v-for="button in buttons">
            <el-button class="guidance-button" size="default" :color="btn_color" :disabled="button.disabled" round>
              <el-icon :size="18">
                <component :is="button.component" />
              </el-icon>
              <span class="btn-text">{{ button.name }}</span>
            </el-button>
          </a>
        </el-row>
      </el-col>
    </el-row>

  </div>
</template>

<style scoped>

/* 文章标题字体、字间距、居中排布、字号 */
.paper-title {
  font-family: "MyFont", Verdana, sans-serif;
  letter-spacing: 2px;
  font-size: 42px;
  margin: 0;
  text-align: center;
  line-height: 64px; /* 与 logo 高度对齐 */
}

/* 姓名和地址按钮 - 减小外边距让作者名更紧凑 */
.title-button {
  margin: 2px 0px; /* 进一步减小上下和左右间距 */
  padding: 4px 6px; /* 减小按钮内边距 */
}

/* 姓名和地址按钮光标悬浮 - 调整悬浮时的间距 */
.title-button:hover {
  margin: 2px 0px; /* 保持和正常状态一致，避免悬浮时跳动 */
}

/* 引导材料按钮 */
.guidance-button {
  margin: 8px 5px;
  box-shadow: #d8d8d8 1px 1px 1px 1px;
}

/* 姓名属性 - 减小字体大小增强紧凑感 */
.author {
  font-size: 16px; /* 从18px减小到16px */
  margin-left: 1px; /* 减小左侧间距 */
  line-height: 1.2; /* 添加紧凑行间距 */
}

/* 姓名上标属性 - 减小上标与姓名的间距 */
.name_sup {
  color: #606266; 
  margin-left: 1px; /* 保持1px */
  font-size: 12px; /* 减小上标字体 */
}

/* 地址属性 */
.address {
  font-size: 16px; /* 从18px减小到16px */
  line-height: 1.2; /* 添加紧凑行间距 */
}

/* 地址上标属性 */
.address_sup {
  color: #606266; 
  margin-right: 1px;
  font-size: 12px; /* 减小上标字体 */
}

/* 头像属性 */
.el-avatar {
  margin-right: 6px;
  box-shadow: #b7b7b7 0px 0px 3px 1px;
}

/* 共一和通讯文字属性 */
.con-cor {
  font-family: Arial;
  font-size: 14px; /* 从16px减小到14px */
  margin: 12px 0px; /* 从18px减小到12px */
  text-align: center;
  line-height: 1.3; /* 添加紧凑行间距 */
}

/* 强调信息属性 */
.emphasis {
  color: chocolate;
  font-weight: bold;
  margin: 8px;
  font-size: 22px;
  text-align: center;
}

/* 引导材料按钮文字属性 */
.btn-text {
  font-size: 18px;
  color: #ffffff;
}

.el-alert {
  margin: 10px 0 0;
}

.el-alert:first-child {
  margin: 0;
}


/* 使 logo 与标题水平排列并垂直居中 */
/* 使 logo 与标题水平排列并垂直居中，并优化间距 */
.title-with-logo {
  display: flex;
  align-items: center;       /* 垂直居中 */
  justify-content: center;   /* 水平居中 */
  gap: 12px;                 /* 调整间距 */
}

.logo-inline {
  max-width: 180px;      /* 放大图片以与标题高度匹配 */
  height: auto;          /* 按比例自适应高度 */
  object-fit: contain;   /* 保证完整显示 */
  display: block;
  align-self: center;    /* 确保垂直居中对齐标题 */
}

/* 手机端链接样式处理 */
a:-webkit-any-link {
  text-decoration: none;
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

/* 作者超链接颜色 */
a.author-link {
  color: #303136 !important; /* 使用蓝色并提高优先级 */
  text-decoration: none; 
  transition: color 0.2s ease; 
}

a.author-link:hover {
  color: #1d4ed8 !important; /* 悬浮时深蓝色，提高优先级 */
  text-decoration: none; 
}

/* 作者按钮内的文字颜色 */
a.author-link .author {
  color: #242425 !important; /* 直接控制作者文字颜色 */
}

a.author-link:hover .author {
  color: #1d4ed8 !important; /* 悬浮时作者文字颜色 */
}

/* 机构超链接颜色 */
a.address-link {
  color: #303136 !important; /* 与作者链接保持一致的颜色 */
  text-decoration: none; 
  transition: color 0.2s ease; 
}

a.address-link:hover {
  color: #1d4ed8 !important; /* 悬浮时深蓝色，提高优先级 */
  text-decoration: none; 
}

/* 机构按钮内的文字颜色 */
a.address-link .address {
  color: #242425 !important; /* 直接控制机构文字颜色 */
}

a.address-link:hover .address {
  color: #1d4ed8 !important; /* 悬浮时机构文字颜色 */
}

</style>