<template>
  <div class="item">
    <h2 class="title green">{{ title }}</h2>
    <p class="description">{{ description }}</p>
    <p v-if="language">language : {{ language }}</p>
    <div class="tags">
      <span v-for="(tag, index) in tags" :key="index" class="tag">{{ tag }}</span>
    </div>
    <div class="links">
      <a v-if="homepage" :href="homepage" target="_blank" rel="noopener noreferrer">Demo</a>
      <a :href="urlLink" target="_blank" rel="noopener noreferrer">Source</a>
    </div>
    <svg class="icon" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
      <path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"></path>
    </svg>
  </div>
</template>

<script>
export default {
  name: 'Item',
  props: {
    title: String,
    description: String,
    urlLink: String,
    tags: Array,
    homepage: String,
    language: String
  }
}
</script>

<style scoped>
.item {
  display: flex;
  flex-direction: column;
  position: relative;
  transform: rotate3d(0, 0, 1, -2deg) translateZ(0) scale(1);
  transform-origin: left center;
  transform-style: preserve-3d;
  will-change: transform;
  transition: transform 1.5s cubic-bezier(0.075, 0.82, 0.165, 1);
}

.item:hover {
  transform: rotate3d(0, 1, 0, 0deg) translateZ(0) scale(1);
}

.title {
  margin-bottom: 0.5rem;
}

.description {
  font-size: 0.9rem;
  line-height: 1.2rem;
  margin-bottom: 0.75rem;
}

.tags {
  display: flex;
  flex-wrap: wrap;
}

.tag {
  margin-right: 0.5rem;
  margin-bottom: 0.5rem;
  padding: 0.25rem 0.5rem;
  background-color: #181818;
  border-radius: 0.5rem;
  box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
  font-size: 0.9rem;
  color: #fff;
}

.links {
  display: flex;
  margin-top: 0.75rem;
}

.links a {
  margin-right: 1rem;
  font-size: 0.9rem;
  perspective-origin: left center;
  transform-style: preserve-3d;
  will-change: transform;
  transform: rotate3d(0, 0, 0, 0deg) translateZ(0);
  transition: all 0.25s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

.links a:hover {
  transform: rotate3d(-.25, 1, 0, -30deg) translateZ(2px) scale(1.1);
}

.icon {
  position: absolute;
  top: .5rem;
  right: 1rem;
  width: 25px;
  height: 25px;
}
</style>
