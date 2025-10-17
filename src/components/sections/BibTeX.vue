<script>
export default {
  data() {
    return {
      bibtex: [
        "@article{junyaohu2023template,",
        "    title={Academic Project Page Template Vue},",
        "    author={Hu, Junyao},",
        "    journal={GitHub},",
        "    year={2023}",
        "}",
      ],
    }
  },
  methods: {
    copyVal() {
      let oInput = document.createElement('textarea');
      let text = document.getElementById('bibtex').innerText;
      oInput.value = text;
      document.body.appendChild(oInput);
      oInput.select();
      document.execCommand('Copy');
      this.$message.success('Copy Successfully');
      oInput.remove();
    }
  }
}

</script>

<template>
  <div class="bibtex-section">
    <div class="bibtex-container">
      <el-divider class="section-divider">
        <span class="section-title">BibTeX</span>
      </el-divider>
      
      <div class="bibtex-content">
        <div class="bibtex-card" @click="copyVal()">
          <div class="copy-hint">
            <svg class="copy-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <rect x="9" y="9" width="13" height="13" rx="2" ry="2"></rect>
              <path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"></path>
            </svg>
            Click to copy BibTeX
          </div>
          <div class="bibtex-code-wrapper">
            <pre id="bibtex" class="bibtex-code"><code v-for="(b, index) in bibtex" :key="index">{{ b }}<br/></code></pre>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>

.bibtex-section {
  background: #fafbfc;
  padding: 40px 20px;
  margin: 0;
}

.bibtex-container {
  max-width: 1200px;
  margin: 0 auto;
}

.section-divider {
  margin: 32px 0 40px;
  border-color: #e2e8f0;
}

.section-title {
  font-size: 28px;
  font-weight: 700;
  color: #1a202c;
  padding: 0 40px;
  background: #fafbfc;
  letter-spacing: -0.02em;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
}

.bibtex-content {
  display: flex;
  justify-content: center;
  padding: 0 20px;
}

.bibtex-card {
  background: #ffffff;
  border-radius: 16px;
  padding: 32px;
  max-width: 800px;
  width: 100%;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.06), 0 2px 4px rgba(0, 0, 0, 0.04);
  border: 1px solid #e2e8f0;
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.bibtex-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.1), 0 6px 12px rgba(0, 0, 0, 0.06);
  border-color: #42b983;
}

.bibtex-card:active {
  transform: translateY(-1px);
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.08), 0 3px 8px rgba(0, 0, 0, 0.05);
}

.copy-hint {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  color: #718096;
  font-size: 15px;
  font-weight: 500;
  margin-bottom: 20px;
  padding: 12px;
  background: linear-gradient(135deg, rgba(66, 185, 131, 0.05), rgba(66, 185, 131, 0.02));
  border-radius: 10px;
  transition: all 0.3s ease;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
}

.bibtex-card:hover .copy-hint {
  color: #42b983;
  background: linear-gradient(135deg, rgba(66, 185, 131, 0.12), rgba(66, 185, 131, 0.06));
}

.copy-icon {
  width: 20px;
  height: 20px;
  stroke: currentColor;
  transition: transform 0.3s ease;
}

.bibtex-card:hover .copy-icon {
  transform: scale(1.1);
}

.bibtex-code-wrapper {
  background: #f7fafc;
  border-radius: 12px;
  padding: 20px;
  border: 1px solid #e2e8f0;
  overflow-x: auto;
}

.bibtex-code {
  margin: 0;
  padding: 0;
  background: transparent;
  border: none;
  font-family: 'Consolas', 'Monaco', 'Courier New', monospace;
  line-height: 1.6;
}

.bibtex-code code {
  font-size: 14px;
  color: #2d3748;
  background: transparent;
  border: none;
  padding: 0;
  display: block;
}

/* 响应式设计 */
@media (max-width: 768px) {
  .bibtex-section {
    padding: 30px 10px;
  }
  
  .section-title {
    font-size: 24px;
    padding: 0 30px;
  }
  
  .bibtex-card {
    padding: 24px 20px;
  }
  
  .copy-hint {
    font-size: 14px;
    padding: 10px;
  }
  
  .bibtex-code-wrapper {
    padding: 16px;
  }
  
  .bibtex-code code {
    font-size: 13px;
  }
}

@media (max-width: 480px) {
  .bibtex-section {
    padding: 20px 5px;
  }
  
  .section-title {
    font-size: 20px;
    padding: 0 20px;
  }
  
  .bibtex-card {
    padding: 20px 16px;
    border-radius: 12px;
  }
  
  .copy-hint {
    font-size: 13px;
    flex-direction: column;
    gap: 6px;
  }
  
  .bibtex-code-wrapper {
    padding: 12px;
  }
  
  .bibtex-code code {
    font-size: 12px;
  }
}

</style>