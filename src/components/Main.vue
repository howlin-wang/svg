<script>
import Title from './sections/Title.vue'
import Abstract from './sections/Abstract.vue'
import Motivation from './sections/Motivation.vue'
import BibTeX from './sections/BibTeX.vue'
import Method from './sections/Method.vue'
import Experiments from './sections/Experiments.vue'
import Comment from './sections/Comment.vue'

export default {
  components: {
    Title,
    Abstract,
    Motivation,
    Method,
    Experiments,
    BibTeX,
    // Comment
  },
  data() {
    return {
      initialSidebarTop: 0,
      abstractTop: 0 // 新增：存储Abstract区块顶部位置
    }
  },
  mounted() {
    // 监听滚动事件实现目录固定效果
    window.addEventListener('scroll', this.handleScroll)
    // 初始化位置
    this.$nextTick(() => {
      this.initializePositions()
      this.handleScroll()
    })
  },
  beforeUnmount() {
    // 移除事件监听
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    initializePositions() {
      const sidebar = document.querySelector('.sidebar-container')
      const abstract = document.querySelector('#abstract')
      
      if (sidebar) {
        this.initialSidebarTop = sidebar.offsetTop
      }
      if (abstract) {
        // 记录Abstract区块的顶部位置作为目录上限
        this.abstractTop = abstract.offsetTop
      }
    },
    handleScroll() {
      const sidebar = document.querySelector('.sidebar-container')
      if (!sidebar) return

      const headerHeight = document.querySelector('header')?.offsetHeight || 0
      const scrollTop = window.scrollY
      const windowHeight = window.innerHeight
      const sidebarHeight = sidebar.offsetHeight

      // 计算固定定位的临界值（基于Abstract顶部）
      const shouldFix = scrollTop >= this.abstractTop - headerHeight

      if (shouldFix) {
        // 确保目录不会超出视口底部，同时顶部不超过Abstract区域
        const maxTop = windowHeight - sidebarHeight - 20
        // 顶部位置不超过Abstract区块顶部
        const topValue = Math.min(
          headerHeight + 50, 
          maxTop,
          // 关键：限制目录最高位置不超过Abstract顶部
          window.scrollY + (this.abstractTop - scrollTop)
        )
        
        sidebar.classList.add('fixed')
        sidebar.style.top = `${topValue}px`
        // 不设置width，让CSS控制固定宽度
      } else {
        sidebar.classList.remove('fixed')
        sidebar.style.top = ''
      }
    }
  }
}
</script>

<template>
  <!-- Title 占全屏 -->
  <div class="full-width-section">
    <Title/>
  </div>

  <div class="main-container">
    <div class="main-left">
      <!-- 目录容器 -->
      <div class="sidebar-container">
        <ul class="sidebar">
          <li><a href="#abstract">Overview</a></li>
          <li><a href="#motivation">Motivation</a></li>
          <li><a href="#method">Method</a></li>
          <li><a href="#experiments">Experiments</a></li>
          <!-- <li><a href="#comment">Comment</a></li> -->
        </ul>
      </div>
    </div>
    <div class="main-right">
      <div id="abstract"><Abstract/></div>
      <div id="motivation"><Motivation/></div>
      <div id="method"><Method/></div>
      <div id="experiments"><Experiments/></div>
      <!-- <div id="comment"><Comment/></div> -->
    </div>
  </div>

  <!-- BibTeX 占全屏 -->
  <div class="full-width-section">
    <BibTeX/>
  </div>

</template>

<style scoped>
.main-container {
  display: flex;
  width: 100%;
  max-width: 1600px; /* 增加最大宽度 */
  margin: 0 auto; /* 居中显示 */
  padding: 0 15px; /* 减少左右边距 */
  box-sizing: border-box;
}

.main-left {
  width: 200px; /* 增加侧边栏宽度 */
  padding: 10px;
  box-sizing: border-box;
  flex-shrink: 0; /* 防止收缩 */
}

/* 目录容器样式 */
.sidebar-container {
  position: relative;
  transition: all 0.2s ease;
  width: 180px; /* 固定宽度 */
  box-sizing: border-box;
}

/* 固定定位样式 - 滚动到顶部时应用 */
.sidebar-container.fixed {
  position: fixed;
  z-index: 50; /* 降低层级，避免覆盖内容 */
  width: 180px !important; /* 强制固定宽度，防止变化 */
}

.main-right {
  flex: 1;
  padding: 0; /* 移除内边距，让各section自己控制 */
  box-sizing: border-box;
}

.main-right > div {
  width: 100%;
  margin-bottom: 0; /* 移除margin，让各section自己控制间距 */
}

.sidebar {
  list-style: none;
  padding: 16px;
  margin: 0;
  background: #ffffff;
  border-radius: 12px;
  border: 1px solid #e1e4e8;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.08);
  width: 100%; /* 填满容器宽度 */
  box-sizing: border-box;
}

.sidebar li {
  margin-bottom: 6px;
  list-style: none;
}

.sidebar li:last-child {
  margin-bottom: 0;
}

.sidebar a {
  display: block;
  padding: 8px 12px;
  text-decoration: none;
  color: #24292e;
  transition: all 0.2s ease;
  font-weight: 500;
  border-radius: 6px;
  font-size: 14px;
  line-height: 1.5;
  white-space: nowrap; /* 防止文字换行 */
}

.sidebar a:hover {
  color: #42b983;
  background: rgba(66, 185, 131, 0.08);
  transform: translateX(2px);
}

.full-width-section {
  width: 100%;
  box-sizing: border-box;
  padding: 0 20px;
}

/* 去掉 Abstract 上方空白 */
#abstract {
  margin-top: 0;
  padding-top: 0;
}

/* 确保所有section都有统一的对齐 */
#abstract,
#motivation,
#method,
#experiments {
  max-width: 100%;
}
</style>