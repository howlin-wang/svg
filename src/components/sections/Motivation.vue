<script setup>
import motivation from '../mds/motivation.mdx';
</script>

<template>
  <div class="section-container">
    <el-divider class="section-divider">
      <span class="section-title">Motivation: Bottleneck of VAE</span>
    </el-divider>

    <el-row justify="center">
      <el-col :xs="24" :sm="24" :md="24" :lg="22" :xl="20" class="content-col">
        <div class="content-wrapper">
          <motivation />
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<style scoped>
.section-container {
  margin: 40px 0;
  padding: 0 10px;
}

.section-divider {
  margin: 32px 0 24px;
  border-color: #d1d5db;
}

.section-title {
  font-size: 28px;
  font-weight: 700;
  color: #111827;
  padding: 0 20px;
  background: #fff;
  letter-spacing: -0.5px;
}

.content-col {
  margin-bottom: 20px;
}

.content-wrapper {
  background: #ffffff;
  border-radius: 12px;
  padding: 32px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.08), 0 1px 2px rgba(0, 0, 0, 0.06);
  border: 1px solid #e5e7eb;
  line-height: 1.75;
}

/* 优化内容样式 */
.content-wrapper :deep(h1),
.content-wrapper :deep(h2),
.content-wrapper :deep(h3) {
  margin-top: 28px;
  margin-bottom: 16px;
  color: #1f2937;
  font-weight: 700;
  line-height: 1.3;
  letter-spacing: -0.3px;
}

.content-wrapper :deep(h1) {
  font-size: 26px;
}

.content-wrapper :deep(h2) {
  font-size: 22px;
}

.content-wrapper :deep(h3) {
  font-size: 18px;
}

.content-wrapper :deep(h1:first-child),
.content-wrapper :deep(h2:first-child),
.content-wrapper :deep(h3:first-child) {
  margin-top: 0;
}

.content-wrapper :deep(p) {
  margin-bottom: 18px;
  color: #374151;
  font-size: 16px;
  line-height: 1.75;
  text-align: left;
}

.content-wrapper :deep(strong) {
  color: #111827;
  font-weight: 600;
}

.content-wrapper :deep(em) {
  color: #4b5563;
  font-style: italic;
}

.content-wrapper :deep(blockquote) {
  margin: 24px 0;
  padding: 16px 20px;
  background: #f9fafb;
  border-left: 4px solid #42b983;
  border-radius: 4px;
  color: #4b5563;
  font-style: italic;
}

.content-wrapper :deep(blockquote p) {
  margin-bottom: 0;
}

.content-wrapper :deep(ul),
.content-wrapper :deep(ol) {
  margin-bottom: 20px;
  padding-left: 28px;
}

.content-wrapper :deep(li) {
  margin-bottom: 10px;
  color: #374151;
  font-size: 16px;
  line-height: 1.75;
}

.content-wrapper :deep(li:last-child) {
  margin-bottom: 0;
}

.content-wrapper :deep(code) {
  background: #f3f4f6;
  padding: 2px 6px;
  border-radius: 4px;
  font-size: 14px;
  color: #e83e8c;
  font-family: 'Monaco', 'Menlo', 'Consolas', monospace;
}
</style>