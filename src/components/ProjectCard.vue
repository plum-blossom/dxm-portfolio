<script setup>
defineProps({
  title: String,
  description: String,
  image: String,
  tags: {
    type: Array,
    default: () => []
  },
  link: String
})
</script>

<template>
  <div class="project-card glass-card">
    <div class="project-image">
      <img :src="image" :alt="title" />
      <div class="project-overlay">
        <a :href="link" class="project-link">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6M15 3h6v6M10 14L21 3"/>
          </svg>
        </a>
      </div>
    </div>
    <div class="project-content">
        <h3 class="project-title">{{ title }}</h3>
        <p class="project-description">{{ description }}</p>
        <div class="project-tags">
          <span v-for="(tag, index) in tags" :key="index" class="tag">
            {{ tag }}
          </span>
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
  margin-bottom: 0.75rem;
  color: var(--text-primary);
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
</style>
