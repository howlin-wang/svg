<script>
import Title from './sections/Title.vue'
import Abstract from './sections/Abstract.vue'
import Motivation from './sections/Motivation.vue'
import BibTeX from './sections/BibTeX.vue'
import Method from './sections/Method.vue'
import Experiments from './sections/Experiments.vue'
import Discussion from './sections/Discussion.vue'
// import Comment from './sections/Comment.vue'

export default {
  components: {
    Title,
    Abstract,
    Motivation,
    Method,
    Experiments,
    Discussion,
    BibTeX,
    // Comment
  },
  data() {
    return {
      abstractTop: 0,
      headerHeight: 0
    }
  },
  mounted() {
    // Wait for the DOM to be fully rendered to get accurate positions
    this.$nextTick(() => {
      this.initializePositions()
      window.addEventListener('scroll', this.handleScroll)
      window.addEventListener('resize', this.handleResize)
    })
  },
  beforeUnmount() {
    // Clean up the event listeners
    window.removeEventListener('scroll', this.handleScroll)
    window.removeEventListener('resize', this.handleResize)
  },
  methods: {
    initializePositions() {
      const abstractEl = document.querySelector('#abstract')
      const headerEl = document.querySelector('header') // Assuming you have a <header> element
      
      if (abstractEl) {
        // Record the top position of the main content area
        this.abstractTop = abstractEl.offsetTop
      }
      if (headerEl) {
        this.headerHeight = headerEl.offsetHeight
      }
    },
    handleScroll() {
      const sidebar = document.querySelector('.sidebar-container')
      if (!sidebar) return

      // 在移动端(屏幕宽度 <= 768px)不执行固定侧边栏逻辑
      if (window.innerWidth <= 768) {
        sidebar.classList.remove('fixed')
        sidebar.style.top = ''
        return
      }

      const scrollTop = window.scrollY

      // The point where the sidebar should become fixed.
      // It's the top of the abstract section minus the header's height and a small margin.
      const fixThreshold = this.abstractTop - this.headerHeight - 50 // 50px margin from top

      if (scrollTop >= fixThreshold) {
        sidebar.classList.add('fixed')
        // Set a fixed top position relative to the viewport
        sidebar.style.top = `${this.headerHeight + 50}px`
      } else {
        sidebar.classList.remove('fixed')
        // Reset the top style to allow it to scroll naturally with the page
        sidebar.style.top = ''
      }
    },
    handleResize() {
      // 重新计算位置以适应窗口大小变化
      this.initializePositions()
      // 触发一次滚动处理以更新侧边栏状态
      this.handleScroll()
    }
  }
}
</script>

<template>
  <div class="full-width-section">
    <Title/>
  </div>

  <div class="main-container">
    <div class="main-left">
      <div class="sidebar-container">
        <div class="sidebar">
          <div class="sidebar-title">Content</div>
          <ul class="sidebar-list">
            <li><a href="#abstract">Overview</a></li>
            <li><a href="#motivation">Motivation</a></li>
            <li><a href="#method">Method</a></li>
            <li><a href="#experiments">Experiments</a></li>
            <li><a href="#discussion">Discussion</a></li>
          </ul>
        </div>
      </div>
    </div>
    <div class="main-right">
      <div style="padding-top: 20px;"> <div id="abstract"><Abstract/></div>
      </div>
      <div id="motivation"><Motivation/></div>
      <div id="method"><Method/></div>
      <div id="experiments"><Experiments/></div>
      <div id="discussion"><Discussion/></div>
      </div>
  </div>

  <div class="full-width-section">
    <BibTeX/>
  </div>
</template>

<style scoped>
.main-container {
  display: flex;
  width: 100%;
  max-width: 1600px;
  margin: 0 auto;
  padding: 0 15px;
  box-sizing: border-box;
}

.main-left {
  width: 200px;
  padding: 10px;
  box-sizing: border-box;
  flex-shrink: 0;
  /* Add a height to ensure it doesn't collapse, though content should handle this */
  align-self: flex-start; /* Align to the top */
}

.sidebar-container {
  position: relative;
  transition: top 0.2s ease; /* Smooth transition for position changes */
  width: 180px;
  box-sizing: border-box;
}

/* Updated fixed positioning style */
.sidebar-container.fixed {
  position: fixed;
  z-index: 50;
  /* The width is already set on the element, no !important needed */
}

.main-right {
  flex: 1;
  padding: 0;
  box-sizing: border-box;
  min-width: 0; /* Prevents flexbox overflow issues */
}

.main-right > div {
  width: 100%;
  margin-bottom: 0;
}

.sidebar {
  padding: 24px 12px;
  margin: 0;
  background: transparent;
  border-radius: 0;
  border: none;
  box-shadow: none;
  width: 100%;
  box-sizing: border-box;
}

.sidebar-title {
  font-size: 16px;
  font-weight: 700;
  color: #2d3748;
  margin-bottom: 16px;
  padding-bottom: 12px;
  border-bottom: 2px solid #42b983;
  text-align: left;
  letter-spacing: 0.02em;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  text-transform: uppercase;
}

.sidebar-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.sidebar-list li {
  margin-bottom: 4px;
  list-style: none;
}

.sidebar-list li:last-child {
  margin-bottom: 0;
}

.sidebar-list a {
  display: flex;
  align-items: center;
  padding: 10px 12px;
  text-decoration: none;
  color: #5a6978;
  transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
  font-weight: 500;
  border-radius: 6px;
  font-size: 15px;
  line-height: 1.6;
  white-space: nowrap;
  position: relative;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
}

.sidebar-list a::before {
  content: '';
  position: absolute;
  left: 0;
  top: 50%;
  transform: translateY(-50%);
  width: 3px;
  height: 0;
  background: #42b983;
  border-radius: 0 3px 3px 0;
  transition: height 0.25s ease;
}

.sidebar-list a:hover {
  color: #42b983;
  background: rgba(66, 185, 131, 0.08);
  transform: translateX(3px);
  padding-left: 16px;
}

.sidebar-list a:hover::before {
  height: 70%;
}

.sidebar-list a:active {
  transform: translateX(2px);
}

.full-width-section {
  width: 100%;
  box-sizing: border-box;
  padding: 0 20px;
}

/* Note: Styles for #abstract, #motivation, etc., remain the same */
#abstract,
#motivation,
#method,
#experiments,
#discussion {
  max-width: 100%;
}

/* 响应式设计 */
@media (max-width: 1024px) {
  .main-container {
    max-width: 100%;
  }
  
  .main-left {
    width: 180px;
  }
  
  .sidebar-container {
    width: 160px;
  }
}

@media (max-width: 768px) {
  .main-container {
    flex-direction: column;
    padding: 0 10px;
  }
  
  .main-left {
    width: 100%;
    padding: 12px 0;
  }
  
  .sidebar-container {
    position: static !important;
    width: 100%;
    margin-bottom: 24px;
  }
  
  .sidebar-container.fixed {
    position: static !important;
  }
  
  .sidebar {
    padding: 16px 12px;
    background: rgba(255, 255, 255, 0.95);
    border-radius: 12px;
    border: 1px solid #e2e8f0;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.04);
  }
  
  .sidebar-title {
    font-size: 15px;
    margin-bottom: 14px;
    padding-bottom: 10px;
    text-align: center;
  }
  
  .sidebar-list {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    flex-wrap: wrap;
    gap: 10px;
  }
  
  .sidebar-list li {
    margin-bottom: 0;
    margin-right: 0;
  }
  
  .sidebar-list a {
    padding: 8px 12px;
    font-size: 13px;
    white-space: nowrap;
  }
  
  .sidebar-list a::before {
    display: none;
  }
  
  .sidebar-list a:hover {
    transform: scale(1.05);
    padding-left: 12px;
  }
  
  .main-right {
    padding: 0;
  }
}

@media (max-width: 480px) {
  .main-container {
    padding: 0 5px;
  }
  
  .sidebar {
    padding: 12px 10px;
  }
  
  .sidebar-title {
    font-size: 14px;
    margin-bottom: 12px;
    text-align: center;
  }
  
  .sidebar-list {
    gap: 8px;
  }
  
  .sidebar-list a {
    padding: 6px 10px;
    font-size: 12px;
  }
}
</style>