<script setup>
defineProps({
  title: String,
  description: String,
  image: String,
  tags: {
    type: Array,
    default: () => [],
  },
  link: String,
  companyProject: Boolean,
  demoLinks: {
    type: Array,
    default: () => [],
  },
});
</script>

<template>
  <div class="project-card glass-card">
    <div class="project-image">
      <img :src="image" :alt="title" />
      <div class="project-overlay">
        <a :href="link" class="project-link">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6M15 3h6v6M10 14L21 3" />
          </svg>
        </a>
      </div>
    </div>
    <div class="project-content">
      <h3 class="project-title">{{ title }}</h3>
      <p v-if="companyProject" class="company-project-note">
        由于保密协议，无法提供源码，但在面试中可详细讲解架构设计。
      </p>
      <p class="project-description">{{ description }}</p>
      <div class="project-tags">
        <span v-for="(tag, index) in tags" :key="index" class="tag">
          {{ tag }}
        </span>
      </div>

      <!-- Demo链接 -->
      <div v-if="demoLinks && demoLinks.length > 0" class="demo-links">
        <div v-for="(demo, index) in demoLinks" :key="index" class="demo-link-item">
          <a v-if="demo.sourceCode" :href="demo.sourceCode" target="_blank" class="demo-link source-code">
            <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path
                d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"
              ></path>
            </svg>
            {{ demo.name }}源码
          </a>
          <a v-if="demo.demoLink" :href="demo.demoLink" target="_blank" class="demo-link demo-site">
            <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6M15 3h6v6M10 14L21 3" />
            </svg>
            {{ demo.name }}演示
          </a>
        </div>
      </div>

      <a :href="link" class="view-project-btn">查看项目</a>
    </div>
  </div>
</template>

<style scoped>
.project-card {
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

.project-image {
  position: relative;
  height: 220px;
  overflow: hidden;
}

.project-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.project-card:hover .project-image img {
  transform: scale(1.05);
}

.project-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(168, 85, 247, 0.8), rgba(236, 72, 153, 0.8));
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.project-card:hover .project-overlay {
  opacity: 1;
}

.project-link {
  width: 56px;
  height: 56px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: white;
  border-radius: 50%;
  color: var(--purple-primary);
  transform: scale(0.8);
  transition: transform 0.3s ease;
}

.project-card:hover .project-link {
  transform: scale(1);
}

.project-link:hover {
  color: var(--purple-secondary);
}

.project-content {
  padding: 1.5rem;
  flex: 1;
  display: flex;
  flex-direction: column;
}

.project-title {
  font-size: 1.25rem;
  margin-bottom: 0.5rem;
  color: var(--text-primary);
}

.company-project-note {
  font-size: 0.8rem;
  color: var(--text-muted);
  margin-bottom: 0.75rem;
  font-style: italic;
}

.project-description {
  color: var(--text-secondary);
  margin-bottom: 1rem;
  line-height: 1.6;
  flex: 1;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.view-project-btn {
  display: inline-block;
  margin-top: 1rem;
  padding: 0.6rem 1.2rem;
  background: linear-gradient(135deg, var(--purple-primary), var(--purple-secondary));
  color: white;
  border-radius: 50px;
  font-size: 0.9rem;
  font-weight: 600;
  text-align: center;
  transition: all 0.3s ease;
}

.view-project-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 15px rgba(168, 85, 247, 0.4);
}

/* Demo链接样式 */
.demo-links {
  margin-top: 1rem;
  padding-top: 1rem;
  border-top: 1px solid var(--border-color);
}

.demo-link-item {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 0.5rem;
}

.demo-link {
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
  padding: 0.4rem 0.8rem;
  background: var(--bg-glass);
  border: 1px solid var(--border-color);
  border-radius: 6px;
  color: var(--text-primary);
  font-size: 0.85rem;
  transition: all 0.3s ease;
}

.demo-link:hover {
  background: rgba(168, 85, 247, 0.1);
  border-color: var(--purple-primary);
  transform: translateY(-1px);
  box-shadow: 0 2px 8px rgba(168, 85, 247, 0.2);
}

.demo-link.source-code:hover {
  border-color: var(--accent-blue);
  background: rgba(59, 130, 246, 0.1);
  box-shadow: 0 2px 8px rgba(59, 130, 246, 0.2);
}

.demo-link.demo-site:hover {
  border-color: var(--accent-cyan);
  background: rgba(6, 182, 212, 0.1);
  box-shadow: 0 2px 8px rgba(6, 182, 212, 0.2);
}
</style>
