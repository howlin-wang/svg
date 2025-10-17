<script setup>
import motivation from '../mds/motivation.mdx';
</script>

<template>
  <div class="section-container">
    <div class="section-header">
      <h2 class="section-title">Motivation: Bottleneck of VAE</h2>
    </div>

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

.section-header {
  margin-bottom: 32px;
}

.section-title {
  font-size: 28px;
  font-weight: 700;
  color: #42b983;
  margin: 0;
  padding: 0 0 16px 0;
  background: transparent;
  letter-spacing: -0.3px;
  line-height: 1.3;
  position: relative;
  display: inline-block;
  border-bottom: 3px solid #42b983;
}

.content-col {
  margin-bottom: 20px;
}

.content-wrapper {
  background: #ffffff;
  border-radius: 16px;
  padding: 40px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.06), 0 2px 4px rgba(0, 0, 0, 0.04);
  border: 1px solid #e2e8f0;
  line-height: 1.75;
  transition: box-shadow 0.3s ease, transform 0.3s ease;
}

.content-wrapper:hover {
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.08), 0 3px 6px rgba(0, 0, 0, 0.06);
  transform: translateY(-2px);
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

/* 响应式图片样式 */
.content-wrapper :deep(img) {
  max-width: 100%;
  height: auto !important;
  display: block;
  margin: 0 auto;
}

.content-wrapper :deep(figure) {
  margin: 24px 0;
  text-align: center;
}

.content-wrapper :deep(figcaption) {
  margin-top: 12px;
  color: #6b7280;
  font-size: 14px;
  font-style: italic;
}

/* 响应式标题样式 */
@media (max-width: 1024px) {
  .section-title {
    font-size: 24px;
    padding: 0 30px;
  }
}

@media (max-width: 768px) {
  .section-title {
    font-size: 20px;
    padding: 0 20px;
    max-width: 95%;
  }
}

@media (max-width: 480px) {
  .section-title {
    font-size: 18px;
    padding: 0 15px;
    white-space: normal;
    line-height: 1.3;
  }
  
  .content-wrapper {
    padding: 24px 20px;
  }
}
</style>