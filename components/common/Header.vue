<template>
  <header class="header">
    <div class="logo-container">
      <div class="logo">
        <NuxtImg 
          :src="`/images/${logo}`"
          width="76"
          height="76"
          alt="KidsConnect Logo"
          loading="eager"
        />
      </div>
      <div class="site-name">KidsConnect</div>
    </div>
  </header>
</template>

<script setup>
defineProps({
  logo: {
    type: String,
    default: 'logo.svg'
  }
})
</script>

<style scoped>
.header {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 12px 40px;
  gap: 10px;
  
  /* position: fixed; */
  /* width: 1480px; */
  height: 100px;
  width: 100%;
  max-width: 1480px;
  margin: 20px auto 0; 
  /* left: 220px; */
  /* top: 20px; */
  
  background: #70232F;
  border-radius: 15px;
  box-sizing: border-box;
  /* z-index: 1000; */
  
  /* transform: translateX(-50%); */
  left: 50%;
  /* max-width: calc(100% - 40px); */
}

.logo-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 0px;
  gap: 18px;
  
  width: 304px;
  height: 76px;
  
  flex: none;
  order: 0;
  flex-grow: 0;
}

.logo {
  width: 76px;
  height: 76px;
  flex-shrink: 0;
  border-radius: 16px;
  overflow: hidden;
  
  display: flex;
  align-items: center;
  justify-content: center;
}

.site-name {
  width: 210px;
  height: 39px;
  
  font-family: 'Montserrat Alternates', sans-serif;
  font-style: normal;
  font-weight: 600;
  font-size: 32px;
  line-height: 39px;
  color: #FFFFFF;
  
  flex: none;
  order: 1;
  flex-grow: 0;
}
</style>