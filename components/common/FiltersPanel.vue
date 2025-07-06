<template>
  <div class="filters-panel">
    <h3 class="panel-title">Фильтры</h3>

    <div class="filters-container">
      <div class="filter-group">
        <h4 class="group-title">Возраст</h4>
        <div class="select-wrapper">
          <select v-model="selectedAge" class="age-select">
            <option value="any">Любой</option>
            <option value="6-10">6-10 лет</option>
            <option value="12-16">12-16 лет</option>
            <option value="17-21">17-21 лет</option>
          </select>
          <svg class="select-arrow" width="15" height="15" viewBox="0 0 24 24" fill="none"><path d="M7.41 8.59L12 13.17l4.59-4.58L18 10l-6 6-6-6 1.41-1.41z" fill="#333333"/></svg>
        </div>
      </div>

      <div class="filter-group">
        <h4 class="group-title">Пол</h4>
        <div class="gender-options">
          <label class="checkbox-option">
            <input type="checkbox" value="male" v-model="selectedGenders">
            <span class="custom-checkbox"></span>
            <span class="checkbox-text">Мужской</span>
          </label>
          <label class="checkbox-option">
            <input type="checkbox" value="female" v-model="selectedGenders">
            <span class="custom-checkbox"></span>
            <span class="checkbox-text">Женский</span>
          </label>
        </div>
      </div>

      <div class="filter-group">
        <h4 class="group-title">Каталог</h4>
        <div class="catalog-content">
          <div v-for="category in catalogData" :key="category.id" class="catalog-category">
            <button @click="toggleCatalogSection(category.id)" class="category-header">
              <span class="category-name">{{ category.name }}</span>
              <span class="category-count">{{ category.count }}</span>
              <svg :class="['arrow-icon', { 'is-open': openCatalogSections[category.id] }]" width="15" height="15" viewBox="0 0 24 24" fill="none"><path d="M7.41 8.59L12 13.17l4.59-4.58L18 10l-6 6-6-6 1.41-1.41z" fill="#333333"/></svg>
            </button>
            <ul v-show="openCatalogSections[category.id]" class="subcategory-list">
              <li v-for="sub in category.subcategories" :key="sub.id" class="subcategory-item">
                <span class="item-name">{{ sub.name }}</span>
                <span class="item-count">{{ sub.count }}</span>
              </li>
            </ul>
          </div>
        </div>
      </div>
      
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const selectedAge = ref('any');
const selectedGenders = ref([]);

const openCatalogSections = ref({
  power_sports: true,
  martial_arts: true,
});

const toggleCatalogSection = (sectionId) => {
  openCatalogSections.value[sectionId] = !openCatalogSections.value[sectionId];
};

const catalogData = ref([
  {
    id: 'power_sports', 
    name: 'Силовой спорт', 
    count: 3,
    subcategories: [
      { id: 'weightlifting', name: 'Тяжелая атлетика', count: 3 },
      { id: 'powerlifting', name: 'Пауэрлифтинг', count: 1 },
    ],
  },
  {
    id: 'martial_arts', 
    name: 'Единоборства', 
    count: 2,
    subcategories: [
      { id: 'wrestling', name: 'Вольная борьба', count: 1 },
      { id: 'judo', name: 'Дзюдо', count: 1 },
    ],
  },
  {
    id: 'dpi_crafts', 
    name: 'ДПИ и ремесла', 
    subcategories: []
  },
  {
    id: 'technical_design', 
    name: 'Техническое конструирование', 
    subcategories: []
  },
  {
    id: 'literature', 
    name: 'Словесность', 
    
    subcategories: []
  },
  {
    id: 'foreign_languages', 
    name: 'Иностранные языки', 
    
    subcategories: []
  },
  {
    id: 'intellectual_development', 
    name: 'Развитие интеллекта', 
    
    subcategories: []
  },
  {
    id: 'it_tech', 
    name: 'Информационные технологии', 
    
    subcategories: []
  },
  {
    id: 'history_traditions', 
    name: 'История и Традиции', 
    
    subcategories: []
  },
  {
    id: 'pedagogy', 
    name: 'Педагогика', 
    
    subcategories: []
  },
  {
    id: 'music_sound', 
    name: 'Музыка и звук', 
    
    subcategories: []
  },
  {
    id: 'singing', 
    name: 'Пение', 
    
    subcategories: []
  },
  {
    id: 'choreography', 
    name: 'Хореография(танцы)', 
    
    subcategories: []
  },
  {
    id: 'performing_arts', 
    name: 'Зрелищные искусства', 
    
    subcategories: []
  },
  {
    id: 'fashion_style', 
    name: 'Мода и стиль', 
    
    subcategories: []
  },
  {
    id: 'educational_entertainment', 
    name: 'Познавательные развлечения', 
    
    subcategories: []
  },
  {
    id: 'tourism', 
    name: 'Туризм', 
    
    subcategories: []
  },
  {
    id: 'natural_sciences', 
    name: 'Естественные науки', 
    
    subcategories: []
  },
  {
    id: 'people_animals', 
    name: 'Люди и животные', 
    
    subcategories: []
  },
  {
    id: 'aesthetic_sports', 
    name: 'Эстетические виды спорта', 
    
    subcategories: []
  },
  {
    id: 'technical_sports', 
    name: 'Технические виды спорта', 
    
    subcategories: []
  },
  {
    id: 'team_sports', 
    name: 'Командно-игровой спорт', 
    
    subcategories: []
  },
  {
    id: 'individual_sports', 
    name: 'Индивидуально игровой спорт', 
    
    subcategories: []
  },
  {
    id: 'water_sports', 
    name: 'Водные виды спорта', 
    
    subcategories: []
  },
  {
    id: 'athletics_gymnastics', 
    name: 'Лёгкая атлетика и гимнастика', 
    
    subcategories: []
  },
  {
    id: 'physical_education', 
    name: 'Физкультура', 
    
    subcategories: []
  }
]);
</script>

<style scoped>
.filters-panel {
  font-family: 'Montserrat', sans-serif;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  padding: 10px 20px;
  gap: 15px;
  width: 100%;
  background: #FFFFFF;
  border-top: 2px solid #70232F;
  border-radius: 5px;
}

.panel-title {
  font-weight: 600;
  font-size: 24px;
  line-height: 29px;
  color: #333333;
  margin: 10px 0;
}

.filters-container {
  width: 100%;
  display: flex;
  flex-direction: column;
}

.filter-group {
  margin-bottom: 20px;
}

.group-title {
  font-weight: 600;
  font-size: 14px;
  line-height: 17px;
  color: #333333;
  margin: 0 0 15px 0;
}

.select-wrapper {
  box-sizing: border-box;
  position: relative;
  width: 100%;
  padding: 0 10px;
  border-bottom: 1px solid #70232F;
}

.age-select {
  width: 100%;
  padding: 5px 0;
  border: none;
  background-color: transparent;
  font-weight: 400;
  font-size: 14px;
  line-height: 17px;
  color: #333333;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  cursor: pointer;
  outline: none;
}

.select-arrow {
  position: absolute;
  right: 10px;
  top: 50%;
  transform: translateY(-50%);
  pointer-events: none;
}

.gender-options {
  display: flex;
  flex-direction: row;
  gap: 20px;
}

.checkbox-option {
  display: flex;
  align-items: center;
  gap: 5px;
  font-weight: 400;
  font-size: 14px;
  cursor: pointer;
}
.checkbox-option input { display: none; }
.custom-checkbox {
  width: 16px;
  height: 16px;
  border: 1px solid #70232F;
  border-radius: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background-color 0.2s;
  flex-shrink: 0;
}
.custom-checkbox::after {
  content: '';
  width: 8px;
  height: 4px;
  border-left: 2px solid white;
  border-bottom: 2px solid white;
  transform: rotate(-45deg) translateY(-1px);
  opacity: 0;
}
.checkbox-option input:checked + .custom-checkbox { background-color: #70232F; }
.checkbox-option input:checked + .custom-checkbox::after { opacity: 1; }

.catalog-content { display: flex; flex-direction: column; gap: 15px; }
.category-header {
  display: flex;
  align-items: center;
  width: 100%;
  background: none;
  border: none;
  padding: 0;
  cursor: pointer;
}
.category-name { font-weight: 400; font-size: 14px; }
.category-count {
  margin-left: 8px;
  color: #70232F;
  font-weight: 400;
  font-size: 14px;
}
.arrow-icon { margin-left: auto; transition: transform 0.3s ease; }
.arrow-icon.is-open { transform: rotate(180deg); }

.subcategory-list {
  list-style: none;
  padding-left: 15px;
  padding-top: 10px;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.subcategory-item {
  display: flex;
  align-items: center;
  font-weight: 400;
  font-size: 14px;
  line-height: 17px;
  color: #333333;
}
.subcategory-item::before {
  content: '•';
  color: #333333;
  font-size: 20px;
  line-height: 16px;
  margin-right: 10px;
}
.item-count {
  margin-left: auto;
  color: #70232F;
}
</style>
