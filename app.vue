<template>
  <header class="header">
    <div class="header-container">
      <div class="logo-container">
        <div class="logo">
          <svg width="76" height="76" viewBox="0 0 76 76" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect width="76" height="76" rx="16" fill="#681D29"/>
            <path d="M28 25L48 35L38 51L28 25Z" fill="#D86B79"/>
            <circle cx="35" cy="30" r="5" fill="#F7DAAB"/>
            <circle cx="45" cy="40" r="4" fill="#2F050F"/>
          </svg>
        </div>
        <div class="site-name">KidsConnect</div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'AppHeader'
}
</script>

<style scoped>
.header {
  position: fixed;
  top: 20px;
  left: 50%;
  transform: translateX(-50%);
  width: 1480px;
  max-width: 90%;
  height: 100px;
  background: #70232F;
  border-radius: 15px;
  z-index: 1000;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.15);
}

.header-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 100%;
  padding: 12px 40px;
}

.logo-container {
  display: flex;
  align-items: center;
  gap: 18px;
}

.logo {
  width: 76px;
  height: 76px;
  flex-shrink: 0;
}

.site-name {
  font-family: 'Montserrat Alternates', sans-serif;
  font-weight: 600;
  font-size: 32px;
  line-height: 39px;
  color: #FFFFFF;
  white-space: nowrap;
}

/* Адаптив для мобильных устройств */
@media (max-width: 768px) {
  .header {
    height: 80px;
    top: 10px;
  }
  
  .header-container {
    padding: 10px 20px;
  }
  
  .logo {
    width: 60px;
    height: 60px;
  }
  
  .site-name {
    font-size: 24px;
  }
}
</style>