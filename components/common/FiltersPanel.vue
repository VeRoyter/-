<template>
  <div class="filters-panel">
    
    <!-- Фильтр по возрасту -->
    <div class="filter-group">
      <h4>Возраст</h4>
      <div class="filter-options">
        <label class="filter-option">
          <input type="checkbox" v-model="selectedAges" value="any">
          <span class="checkmark"></span>
          Любой
        </label>
      </div>
    </div>
    
    <!-- Фильтр по полу -->
    <div class="filter-group">
      <h4>Пол</h4>
      <div class="filter-options">
        <label class="filter-option">
          <input type="checkbox" v-model="selectedGenders" value="male">
          <span class="checkmark"></span>
          Мужской
        </label>
        <label class="filter-option">
          <input type="checkbox" v-model="selectedGenders" value="female">
          <span class="checkmark"></span>
          Женский
        </label>
      </div>
    </div>
    
    <!-- Фильтр по категориям -->
    <div class="filter-group">
      <h4>Каталог</h4>
      <div class="filter-options">
        <div class="category-header">
          <span>Силовой спорт</span>
          <span class="count">3</span>
        </div>
        <label class="filter-option sub-option">
          <input type="checkbox" v-model="selectedCategories" value="weightlifting">
          <span class="checkmark"></span>
          Тяжелая атлетика
          <span class="count">3</span>
        </label>
        <label class="filter-option sub-option">
          <input type="checkbox" v-model="selectedCategories" value="powerlifting">
          <span class="checkmark"></span>
          Пауэрлифтинг
          <span class="count">1</span>
        </label>
        
        <div class="category-header">
          <span>Единоборства</span>
          <span class="count">2</span>
        </div>
        <label class="filter-option sub-option">
          <input type="checkbox" v-model="selectedCategories" value="wrestling">
          <span class="checkmark"></span>
          Вольная борьба
          <span class="count">1</span>
        </label>
        <label class="filter-option sub-option">
          <input type="checkbox" v-model="selectedCategories" value="judo">
          <span class="checkmark"></span>
          Дзюдо
          <span class="count">1</span>
        </label>
        
        <div v-for="category in otherCategories" :key="category.value" class="category-header">
          <span>{{ category.label }}</span>
        </div>
      </div>
    </div>
    
    <button class="apply-btn">Применить фильтры</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const selectedAges = ref(['any'])
const selectedGenders = ref([])
const selectedCategories = ref([])

const otherCategories = ref([
  { value: 'dpi', label: 'ДПИ и ремесла' },
  { value: 'tech', label: 'Техническое конструирование' },
  { value: 'languages', label: 'Словесность' },
  { value: 'foreign', label: 'Иностранные языки' },
  { value: 'intellect', label: 'Развитие интеллекта' },
  { value: 'it', label: 'Информационные технологии' },
  { value: 'history', label: 'История и Традиции' },
  { value: 'pedagogy', label: 'Педагогика' },
  { value: 'music', label: 'Музыка и звук' },
  { value: 'singing', label: 'Пение' },
  { value: 'choreography', label: 'Хореография' },
  { value: 'art', label: 'Зрелищные искусства' },
  { value: 'fashion', label: 'Мода и стиль' },
  { value: 'entertainment', label: 'Познавательные развлечения' },
  { value: 'tourism', label: 'Туризм' },
  { value: 'science', label: 'Естественные науки' },
  { value: 'animals', label: 'Люди и животные' },
  { value: 'aesthetic', label: 'Эстетические виды спорта' },
  { value: 'technical', label: 'Технические виды спорта' },
  { value: 'team', label: 'Командно-игровой спорт' },
  { value: 'individual', label: 'Индивидуально игровой спорт' },
  { value: 'water', label: 'Водные виды спорта' },
  { value: 'athletics', label: 'Лёгкая атлетика и гимнастика' },
  { value: 'fitness', label: 'Физкультура' }
])
</script>

<style scoped>
.filters-panel {
  background: white;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
}

.filters-title {
  font-family: 'Montserrat', sans-serif;
  font-size: 20px;
  font-weight: 600;
  margin-bottom: 20px;
  color: #2F050F;
}

.filter-group {
  margin-bottom: 25px;
}

.filter-group h4 {
  font-family: 'Montserrat', sans-serif;
  font-size: 16px;
  font-weight: 500;
  margin-bottom: 12px;
  color: #333;
}

.filter-options {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.category-header {
  font-family: 'Montserrat', sans-serif;
  font-weight: 600;
  font-size: 14px;
  margin-top: 15px;
  margin-bottom: 5px;
  display: flex;
  justify-content: space-between;
}

.filter-option {
  display: flex;
  align-items: center;
  gap: 10px;
  font-family: 'Montserrat', sans-serif;
  font-size: 14px;
  color: #555;
  cursor: pointer;
  position: relative;
  padding-left: 28px;
}

.sub-option {
  padding-left: 38px;
  font-size: 13px;
}

.filter-option input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
}

.checkmark {
  position: absolute;
  left: 0;
  height: 18px;
  width: 18px;
  background-color: #f5f5f5;
  border: 1px solid #ddd;
  border-radius: 4px;
}

.filter-option:hover input ~ .checkmark {
  background-color: #f0f0f0;
}

.filter-option input:checked ~ .checkmark {
  background-color: #70232F;
  border-color: #70232F;
}

.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

.filter-option input:checked ~ .checkmark:after {
  display: block;
}

.filter-option .checkmark:after {
  left: 6px;
  top: 2px;
  width: 5px;
  height: 10px;
  border: solid white;
  border-width: 0 2px 2px 0;
  transform: rotate(45deg);
}

.count {
  color: #999;
  margin-left: 5px;
  font-weight: 400;
}

.apply-btn {
  width: 100%;
  padding: 12px;
  background: #70232F;
  color: white;
  border: none;
  border-radius: 4px;
  font-family: 'Montserrat', sans-serif;
  font-weight: 500;
  cursor: pointer;
  transition: background 0.3s;
  margin-top: 10px;
}

.apply-btn:hover {
  background: #5a1c25;
}
</style>