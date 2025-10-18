<script lang="ts" setup>

import { ElIcon } from 'element-plus'
import { Document, Files, MagicStick, Picture, DataAnalysis, Film } from '@element-plus/icons-vue'

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
    name: "Department of Automation, Tsinghua University",
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
  "#: Equal Contribution. Listed in alphabetical order. *: Project Leader.",
  
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
    disabled: false,
    name: "Paper",
    link: "https://github.com/shiml20/SVG",
    component: Document,
  },
  {
    disabled: false,
    name: "Code",
    link: "https://github.com/shiml20/SVG",
    component: Files,
  },
]

</script>

<template>
  <div class="title-section">
    <div class="title-content">
      <!-- 文章标题 -->
      <div class="title-header">
        <h1 class="paper-title">
          <span v-if="title" :style="{color:title_color}">{{ title }}</span>
          <span v-if="title_supp" :style="{color:title_supp_color}">{{ title_supp }}</span>
        </h1>
      </div>

      <!-- 作者名单 -->
      <div class="authors-container">
        <a 
          v-for="author in authors" 
          :key="author.name"
          :href="author.homepage" 
          class="author-link"
          target="_blank"
          rel="noopener noreferrer"
        >
          <span class="author-name">
            {{ author.name }}<sup v-if="author.address_flag" class="name-sup">{{ author.address_flag }}</sup>
          </span>
        </a>
      </div>

      <!-- 地址名单 -->
      <div class="affiliations-container">
        <a 
          v-for="address in addresses" 
          :key="address.address_flag"
          :href="address.homepage" 
          class="affiliation-link"
          target="_blank"
          rel="noopener noreferrer"
        >
          <span class="affiliation-name">
            <sup v-if="address.address_flag" class="address-sup">{{ address.address_flag }}</sup>{{ address.name }}
          </span>
        </a>
      </div>

      <!-- 共一和通讯提示内容 -->
      <div class="contribution-note">
        <p v-for="(line, index) in con_and_corresponding_author" :key="index">
          {{ line }}
        </p>
      </div>

      <!-- 提供引导按钮 -->
      <div class="action-buttons">
        <a 
          v-for="button in buttons" 
          :key="button.name"
          :href="button.link"
          target="_blank"
          rel="noopener noreferrer"
        >
          <button 
            class="action-button" 
            :class="{ disabled: button.disabled }"
            :disabled="button.disabled"
          >
            <el-icon :size="20" class="button-icon">
              <component :is="button.component" />
            </el-icon>
            <span class="button-text">{{ button.name }}</span>
          </button>
        </a>
      </div>
    </div>
  </div>
</template>

<style scoped>

/* 整体容器 */
.title-section {
  background: linear-gradient(135deg, #f8f9fa 0%, #ffffff 100%);
  padding: 60px 20px;
  margin: 0 0 40px 0;
}

.title-content {
  max-width: 1200px;
  margin: 0 auto;
  background: #ffffff;
  border-radius: 24px;
  padding: 48px 40px;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.06), 0 4px 12px rgba(0, 0, 0, 0.04);
  border: 1px solid #e2e8f0;
}

/* 标题区域 */
.title-header {
  margin-bottom: 32px;
}

.paper-title {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  font-weight: 700;
  letter-spacing: -0.02em;
  font-size: 42px;
  margin: 0;
  text-align: center;
  line-height: 1.3;
  color: #1a202c;
  padding: 0 20px;
}

/* 作者容器 */
.authors-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  gap: 8px 16px;
  margin-bottom: 24px;
  padding: 0 20px;
}

.author-link {
  text-decoration: none;
  transition: all 0.25s ease;
  display: inline-block;
}

.author-name {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  font-size: 16px;
  font-weight: 500;
  color: #4a5568;
  transition: color 0.25s ease;
  display: inline-block;
  padding: 6px 12px;
  border-radius: 8px;
  background: transparent;
}

.author-link:hover .author-name {
  color: #42b983;
  background: rgba(66, 185, 131, 0.08);
}

.name-sup {
  color: #718096;
  margin-left: 2px;
  font-size: 12px;
  font-weight: 600;
}

/* 机构容器 */
.affiliations-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  gap: 12px 24px;
  margin-bottom: 20px;
  padding: 0 20px;
}

.affiliation-link {
  text-decoration: none;
  transition: all 0.25s ease;
  display: inline-block;
}

.affiliation-name {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  font-size: 15px;
  font-weight: 500;
  color: #718096;
  transition: color 0.25s ease;
  display: inline-block;
  padding: 4px 10px;
  border-radius: 6px;
}

.affiliation-link:hover .affiliation-name {
  color: #42b983;
  background: rgba(66, 185, 131, 0.06);
}

.address-sup {
  color: #a0aec0;
  margin-right: 3px;
  font-size: 13px;
  font-weight: 600;
}

/* 贡献说明 */
.contribution-note {
  text-align: center;
  margin: 24px 0 32px 0;
  padding: 0 20px;
}

.contribution-note p {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  font-size: 14px;
  color: #718096;
  margin: 6px 0;
  line-height: 1.6;
  font-style: italic;
}

/* 操作按钮容器 */
.action-buttons {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 16px;
  flex-wrap: wrap;
  margin-top: 32px;
  padding: 0 20px;
}

.action-button {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 14px 28px;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  font-size: 16px;
  font-weight: 600;
  color: #ffffff;
  background: linear-gradient(135deg, #42b983 0%, #359268 100%);
  border: none;
  border-radius: 12px;
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: 0 4px 12px rgba(66, 185, 131, 0.3);
  position: relative;
  overflow: hidden;
}

.action-button::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
  transition: left 0.6s ease;
}

.action-button:hover:not(.disabled) {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(66, 185, 131, 0.4);
}

.action-button:hover:not(.disabled)::before {
  left: 100%;
}

.action-button:active:not(.disabled) {
  transform: translateY(0);
}

.action-button.disabled {
  background: linear-gradient(135deg, #cbd5e0 0%, #a0aec0 100%);
  cursor: not-allowed;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
  opacity: 0.6;
}

.button-icon {
  display: flex;
  align-items: center;
}

.button-text {
  font-size: 16px;
}

/* 响应式设计 */
@media (max-width: 1024px) {
  .paper-title {
    font-size: 36px;
  }
  
  .title-content {
    padding: 40px 32px;
  }
}

@media (max-width: 768px) {
  .title-section {
    padding: 40px 15px;
    margin-bottom: 30px;
  }
  
  .title-content {
    padding: 32px 24px;
    border-radius: 20px;
  }
  
  .paper-title {
    font-size: 28px;
    padding: 0 10px;
  }
  
  .authors-container,
  .affiliations-container {
    gap: 6px 12px;
  }
  
  .author-name {
    font-size: 14px;
    padding: 4px 10px;
  }
  
  .affiliation-name {
    font-size: 13px;
    padding: 3px 8px;
  }
  
  .contribution-note p {
    font-size: 12px;
  }
  
  .action-button {
    padding: 12px 24px;
    font-size: 15px;
  }
}

@media (max-width: 480px) {
  .title-section {
    padding: 30px 10px;
  }
  
  .title-content {
    padding: 24px 16px;
    border-radius: 16px;
  }
  
  .paper-title {
    font-size: 22px;
    line-height: 1.4;
  }
  
  .authors-container {
    gap: 4px 8px;
  }
  
  .author-name {
    font-size: 13px;
    padding: 3px 8px;
  }
  
  .affiliation-name {
    font-size: 12px;
  }
  
  .action-buttons {
    flex-direction: column;
    gap: 12px;
  }
  
  .action-button {
    width: 100%;
    justify-content: center;
    padding: 12px 20px;
  }
}

</style>