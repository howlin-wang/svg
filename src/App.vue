<script>

import Header from './components/Header.vue'
import Main from './components/Main.vue'
import Footer from './components/Footer.vue'

export default {
  components: {
    // Header,
    Main,
    Footer,
  }
}

</script>

<template>
    <div>
      
      <el-container>
        <el-header><Header/></el-header>
        <el-main><Main/></el-main>
        <el-footer><Footer/></el-footer>
      </el-container>
      
      <!-- 回到顶部 -->
      <el-backtop :right="40" :bottom="80" />
    </div>
</template>

<style>

/* 标题统一样式 */
h1 {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  font-weight: 700;
  letter-spacing: -0.02em;
  font-size: 32px;
  margin: 0;
  text-align: center;
  color: #1a202c;
  line-height: 1.2;
}

h2 {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  font-weight: 700;
  font-size: 24px;
  letter-spacing: -0.01em;
  color: #2d3748;
  line-height: 1.3;
  margin-top: 2em;
  margin-bottom: 0.8em;
}

h3 {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  font-weight: 600;
  font-size: 20px;
  letter-spacing: -0.01em;
  color: #2d3748;
  line-height: 1.4;
  margin-top: 1.5em;
  margin-bottom: 0.6em;
}

h4, h5, h6 {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  font-weight: 600;
  letter-spacing: -0.01em;
  color: #2d3748;
  line-height: 1.4;
}

.el-header {
  padding: 0;
}

.el-footer {
  padding: 0;
}

.el-main {
  padding: 0;
}

/* 段落和列表样式优化 */
p, li {
  font-size: 16px;
  line-height: 1.75;
  color: #4a5568;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
}

p {
  margin-bottom: 1.25em;
}

/* 代码块样式优化 */
code {
  font-family: 'Consolas', 'Monaco', 'Courier New', monospace;
  border-radius: 6px;
  padding: 3px 6px;
  background: #f7fafc;
  color: #d73a49;
  font-size: 0.9em;
  border: 1px solid #e2e8f0;
}

pre {
  border-radius: 12px;
  padding: 16px;
  background: #f7fafc;
  line-height: 1.6;
  border: 1px solid #e2e8f0;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05);
}

pre:not(pre[id=bibtex]) {
  overflow-x: auto;
}

pre code {
  font-size: 14px;
  color: #2d3748;
  border: none;
  padding: 0;
  background: transparent;
}

/* 引用块样式优化 */
blockquote {
  border-left: 4px solid #42b983;
  padding: 16px 24px;
  margin: 24px 0;
  background: #f7fafc;
  border-radius: 0 8px 8px 0;
  color: #4a5568;
  font-style: italic;
}

blockquote > p {
  margin-block-start: 0.5em;
  margin-block-end: 0.5em;
}

/* 链接样式优化 */
a {
  color: #42b983;
  text-decoration: none;
  transition: all 0.2s ease;
  font-weight: 500;
}

a:hover {
  color: #359268;
  text-decoration: none;
}

/* 图片样式优化 */
p > img {
  width: 100%;
  max-width: 800px;
  display: block;
  margin: 24px auto;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

p > img:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
}

/* 表格样式优化 */
table {
  border-collapse: collapse;
  width: max-content;
  max-width: 100%;
  margin: 24px auto;
  display: block;
  overflow-x: auto;
  border-radius: 12px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05);
  background: #fff;
}

thead {
  background: #f7fafc;
  border-bottom: 2px solid #e2e8f0;
}

thead th {
  font-weight: 600;
  color: #2d3748;
}

tbody tr {
  border-bottom: 1px solid #e2e8f0;
  transition: background-color 0.2s ease;
}

tbody tr:hover {
  background: #f7fafc;
}

tbody tr:last-child {
  border-bottom: none;
}

th, td {
  padding: 12px 20px;
  text-align: left;
}

/* 数学公式样式 */
.katex-display {
  overflow-x: auto;
  overflow-y: hidden;
  padding: 16px 0;
}

/* 回到顶部按钮样式优化 */
.el-backtop {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  border-radius: 50%;
  background: #42b983 !important;
  transition: all 0.3s ease;
}

.el-backtop:hover {
  background: #359268 !important;
  transform: translateY(-3px);
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.2);
}

</style>