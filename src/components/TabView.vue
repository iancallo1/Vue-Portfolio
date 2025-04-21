<script setup>
import { ref } from 'vue'
import ContactMe from '../Main/ContactMe/ContactMe.vue'

const tabs = [
  { 
    id: 'summary', 
    label: 'THE ADAPT', 
    description: 'Building with Performance Driven Development',
    bgImage: '/path-to-image.jpg'
  },
  { 
    id: 'about', 
    label: 'ABOUT ME',
    description: 'Exploring modern animation techniques'
  },
  { 
    id: 'projects', 
    label: 'MY PROJECTS',
    description: 'Creative visual effects'
  },
  { 
    id: 'contact', 
    label: 'CONTACT ME',
    description: 'Dynamic interface design'
  }
]

const hoveredTab = ref(null)
const activeTab = ref(null)

const handleHover = (tabId) => {
  hoveredTab.value = tabId
}

const handleLeave = () => {
  hoveredTab.value = null
}
</script>

<template>
  <div class="layout-container">
    <div class="tabs-container">
      <div
        v-for="tab in tabs"
        :key="tab.id"
        class="tab-section"
        :class="{ 'hovered': hoveredTab === tab.id }"
        @mouseenter="handleHover(tab.id)"
        @mouseleave="handleLeave"
      >
        <div class="tab-content">
          <h2 class="tab-title">{{ tab.label }}</h2>
          <div class="tab-description" v-show="hoveredTab === tab.id">
            <p>{{ tab.description }}</p>
            <div class="content-area">
              <ContactMe v-if="tab.id === 'contact'" />
              <!-- Add other content components here -->
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.layout-container {
  width: 100vw;
  height: 100vh;
  background: #0a0a0a;
  position: fixed;
  top: 0;
  left: 0;
  overflow: hidden;
}

.tabs-container {
  display: flex;
  height: 100%;
  width: 100%;
  min-width: min-content;
}

.tab-section {
  flex: 1;
  min-width: 300px;
  height: 100%;
  transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
  cursor: pointer;
  display: flex;
  flex-direction: column;
  padding: 2rem;
  border-right: 2px solid rgba(255, 255, 255, 0.15);
}

/* Alternating background colors for tabs */
.tab-section:nth-child(1) { background: #111111; }
.tab-section:nth-child(2) { background: #141414; }
.tab-section:nth-child(3) { background: #171717; }
.tab-section:nth-child(4) { background: #1a1a1a; }

.tab-section:last-child {
  border-right: none;
}

.tab-section:hover {
  background: #1e1e1e;
}

.tab-section.hovered {
  flex: 2.5;
  min-width: 600px;
  background: #1e1e1e;
  box-shadow: 0 0 30px rgba(0, 0, 0, 0.5);
  z-index: 2;
}

.tab-section:not(.hovered) {
  flex: 0.7;
  min-width: 100px;
  opacity: 0.8;
}

.tab-content {
  height: 100%;
  display: flex;
  flex-direction: column;
  position: relative;
}

.tab-title {
  writing-mode: vertical-rl;
  text-orientation: mixed;
  transform: rotate(180deg);
  color: #fff;
  font-size: 1.8rem;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  white-space: nowrap;
  transition: all 0.5s ease;
  position: absolute;
  left: 0;
  top: 50%;
  transform-origin: left center;
  transform: rotate(180deg) translateY(50%);
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font-weight: 600;
}

.hovered .tab-title {
  writing-mode: horizontal-tb;
  transform: none;
  font-size: 2.5rem;
  position: relative;
  top: 0;
  margin-bottom: 2rem;
  color: #ffffff;
}

.tab-description {
  opacity: 0;
  transform: translateY(20px);
  transition: all 0.5s ease;
  color: #999;
  overflow-y: auto;
  height: 100%;
  padding-right: 1rem;
}

.hovered .tab-description {
  opacity: 1;
  transform: translateY(0);
}

.content-area {
  margin-top: 2rem;
  max-width: 800px;
}

/* Hover effects */
.tabs-container:hover .tab-section:not(.hovered) {
  opacity: 0.5;
}

/* Smooth scrollbar styling */
.tab-description::-webkit-scrollbar {
  width: 6px;
}

.tab-description::-webkit-scrollbar-track {
  background: rgba(255, 255, 255, 0.1);
  border-radius: 3px;
}

.tab-description::-webkit-scrollbar-thumb {
  background: rgba(255, 255, 255, 0.2);
  border-radius: 3px;
}

.tab-description::-webkit-scrollbar-thumb:hover {
  background: rgba(255, 255, 255, 0.3);
}

@media (max-width: 1200px) {
  .tabs-container {
    overflow-x: auto;
    overflow-y: hidden;
    scroll-snap-type: x mandatory;
  }

  .tab-section {
    scroll-snap-align: start;
  }
}

@media (max-width: 768px) {
  .tabs-container {
    flex-direction: column;
    overflow-y: auto;
    overflow-x: hidden;
    scroll-snap-type: y mandatory;
  }

  .tab-section {
    min-height: 100px;
    min-width: 100%;
    border-right: none;
    border-bottom: 2px solid rgba(255, 255, 255, 0.15);
  }

  .tab-title {
    writing-mode: horizontal-tb;
    transform: none;
    position: relative;
    top: 0;
    margin-bottom: 1rem;
    font-size: 1.5rem;
  }

  .tab-section.hovered {
    min-height: 400px;
  }

  .tab-section:not(.hovered) {
    min-height: 80px;
  }

  .tab-section:last-child {
    border-bottom: none;
  }
}
</style> 