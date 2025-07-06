<template>
  <nav class="navbar">
    <div class="navbar-container">
      <div class="search-section">
        <div class="search-box">
          <div class="search-icon">
            <svg width="18" height="18" viewBox="0 0 18 18" fill="none">
              <circle cx="8" cy="8" r="6" stroke="#333333" stroke-width="2"/>
              <path d="M12.5 12.5L16 16" stroke="#333333" stroke-width="2" stroke-linecap="round"/>
            </svg>
          </div>
          <span class="search-text">Поиск</span>
        </div>
        
        <div class="filter-buttons">
          <button class="filter-btn">Все</button>
          <button class="filter-nonactive-btn">Платные</button>
          <button class="filter-nonactive-btn">Бесплатные</button>
        </div>
      </div>
      
      <button class="map-btn">
        <span>На карте</span>
        <div class="map-icon">
          <svg width="18" height="18" viewBox="0 0 18 18" fill="none">
            <path d="M9 1.5C6.1005 1.5 3.75 3.8505 3.75 6.75C3.75 11.25 9 16.5 9 16.5C9 16.5 14.25 11.25 14.25 6.75C14.25 3.8505 11.8995 1.5 9 1.5ZM9 8.625C8.004 8.625 7.125 7.746 7.125 6.75C7.125 5.754 8.004 4.875 9 4.875C9.996 4.875 10.875 5.754 10.875 6.75C10.875 7.746 9.996 8.625 9 8.625Z" fill="#70232F"/>
          </svg>
        </div>
      </button>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  display: flex;
  justify-content: center;
  /* padding: 0 20px; */
  /* margin: 20px 0; */
}

.navbar-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 0px;
  gap: 20px;
  width: 1400px;
  height: 40px;
}

.search-section {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 0px;
  gap: 20px;
  width: 547px;
  height: 40px;
}

.search-box {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 0px;
  gap: 11px;
  width: 241px;
  height: 40px;
  background: #FFFFFF;
  border-radius: 5px;
  padding-left: 17.85px;
  position: relative;
  cursor: pointer;
  transition: box-shadow 0.3s;
}

.search-box:hover {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.search-icon {
  width: 18px;
  height: 18px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.search-text {
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 17px;
  letter-spacing: -0.01em;
  color: #D86B79;
}

.filter-buttons {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 0px;
  gap: 20px;
  width: 287px;
  height: 40px;
}

.filter-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 20px;
  gap: 10px;
  height: 40px;
  background: #FFFFFF;
  border-radius: 5px;
  border: none;
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 20px;
  color: #333333;
  cursor: pointer;
  transition: all 0.3s;
  white-space: nowrap;
}

.filter-nonactive-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 20px;
  gap: 10px;
  height: 40px;
  border-radius: 5px;
  border: none;
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 20px;
  color: #333333;
  cursor: pointer;
  transition: all 0.3s;
  white-space: nowrap;
}

.filter-btn:hover {
  background: #f5f5f5;
}

.filter-btn.active {
  background: #70232F;
  color: white;
}

.map-btn {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 10px 20px;
  gap: 10px;
  width: 141px;
  height: 40px;
  background: #FFFFFF;
  border-radius: 5px;
  border: none;
  cursor: pointer;
  transition: all 0.3s;
}

.map-btn:hover {
  background: #f5f5f5;
}

.map-btn span {
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 20px;
  color: #333333;
}

.map-icon {
  width: 18px;
  height: 18px;
  display: flex;
  align-items: center;
  justify-content: center;
}

@media (max-width: 1440px) {
  .navbar-container {
    width: 100%;
  }
}

@media (max-width: 992px) {
  .navbar-container {
    flex-wrap: wrap;
    height: auto;
    justify-content: center;
  }
  .search-section {
    flex-grow: 1;
  }
}

@media (max-width: 768px) {
  .navbar-container {
    flex-direction: column;
    align-items: stretch;
    gap: 15px;
  }
  
  .search-section {
    flex-direction: column;
    width: 100%;
    height: auto;
    gap: 10px;
    order: 2;
  }
  
  .search-box {
    width: 100%;
  }
  
  .filter-buttons {
    width: 100%;
    justify-content: space-between;
    gap: 10px;
  }
  
  .filter-btn {
    flex: 1;
    padding: 10px 5px;
    font-size: 14px;
  }
  
  .map-btn {
    width: 100%;
    justify-content: center;
    order: 1;
  }
}

@media (max-width: 576px) {
  .navbar-container {
    flex-direction: column;
    height: auto;
    gap: 15px;
  }
  
  .map-btn {
    width: 100%;
  }
}
</style>