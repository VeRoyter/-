<template>
  <div class="program-card">
    <button @click="toggleProgramVisibility" class="main-header-button">
      <h3 class="main-header">СОДЕРЖАНИЕ ПРОГРАММЫ</h3>
      <svg :class="['arrow-icon', { 'is-open': isProgramVisible }]" width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M7.41 8.59L12 13.17L16.59 8.59L18 10L12 16L6 10L7.41 8.59Z" fill="#333333"/>
      </svg>
    </button>

    <div v-show="isProgramVisible" class="program-list">
  
      <div v-for="(item, index) in program" :key="index" class="program-item">

        <button @click="toggleSection(index)" class="item-header">
          <span class="item-title">{{ item.title }}</span>
          <svg :class="['arrow-icon', { 'is-open': openSections[index] }]" width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M7.41 8.59L12 13.17L16.59 8.59L18 10L12 16L6 10L7.41 8.59Z" fill="#333333"/>
          </svg>
        </button>

        <div v-show="openSections[index]" class="item-content">
          <p>{{ item.content }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({
  program: {
    type: Array,
    required: true,
    default: () => []
  }
});

const isProgramVisible = ref(true);

const openSections = ref({});

props.program.forEach((_, index) => {
  openSections.value[index] = true;
});

const toggleProgramVisibility = () => {
  isProgramVisible.value = !isProgramVisible.value;
};

const toggleSection = (index) => {
  openSections.value[index] = !openSections.value[index];
};
</script>

<style scoped>
.program-card {
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 20px;
  gap: 25px;
  background: #FFFFFF;
  border-top: 2px solid #70232F;
  border-radius: 5px;
  width: 100%;
}

.main-header-button {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  background: none;
  border: none;
  padding: 0;
  cursor: pointer;
}

.main-header {
  font-family: 'Montserrat', sans-serif;
  font-weight: 600;
  font-size: 18px;
  line-height: 22px;
  text-transform: uppercase;
  color: #70232F;
  margin: 0;
}

.program-list {
  display: flex;
  flex-direction: column;
  width: 100%;
  gap: 20px;
  padding-top: 10px;
}

.program-item {
  display: flex;
  flex-direction: column;
  width: 100%;
}

.item-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  background: none;
  border: none;
  padding: 0;
  cursor: pointer;
  margin-bottom: 10px;
}

.item-title {
  font-family: 'Montserrat', sans-serif;
  font-weight: 600;
  font-size: 16px;
  line-height: 20px;
  color: #70232F;
}

.arrow-icon {
  transition: transform 0.3s ease;
  flex-shrink: 0;
}
.arrow-icon.is-open {
  transform: rotate(180deg);
}

.item-content {
  padding: 0 10px;
}
.item-content p {
  font-family: 'Montserrat', sans-serif;
  font-weight: 400;
  font-size: 14px;
  line-height: 1.6;
  color: #333333;
  margin: 0;
  white-space: pre-wrap;
}
</style>
