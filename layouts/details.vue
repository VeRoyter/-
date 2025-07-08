<template>
  <div class="page-container">
    <CommonHeader logo="logo_2.svg" />
    <div class="content-container">
      <!-- <CommonNavbar /> -->
      <EventNav />
      <main>
        <slot />
      </main>
    </div>
  </div>
</template>

<style scoped>
.page-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  max-width: 1480px;
  margin: auto;
}

.content-container {
  display: flex;
  flex-direction: column;
  gap: 20px;
  background: #EFEFEF;
  border-radius: 15px;
  padding: 40px;
  margin-top: 20px;
}

</style>
