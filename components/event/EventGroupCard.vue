<template>
  <div class="cards-wrapper">
    <div class="card">
      <div class="card-content">
        <div class="upp">
          <div class="header">ГРУППЫ</div>
          <div class="subheader">{{ group.name }}</div>

          <span class="info-row"> 
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M12 12C13.6569 12 15 10.6569 15 9C15 7.34315 13.6569 6 12 6C10.3431 6 9 7.34315 9 9C9 10.6569 10.3431 12 12 12ZM12 14C8.13401 14 5 17.134 5 21H19C19 17.134 15.866 14 12 14Z" fill="#70232F"/></svg>
            {{ group.coach }}
          </span>
          <span class="info-row">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M16 11C17.6569 11 19 9.65685 19 8C19 6.34315 17.6569 5 16 5C14.3431 5 13 6.34315 13 8C13 9.65685 14.3431 11 16 11ZM8 11C9.65685 11 11 9.65685 11 8C11 6.34315 9.65685 5 8 5C6.34315 5 5 6.34315 5 8C5 9.65685 6.34315 11 8 11ZM16 13C13.3431 13 11 15.2386 11 18H21C21 15.2386 18.6569 13 16 13ZM8 13C5.34315 13 3 15.2386 3 18H11C11 15.2386 8.65685 13 8 13Z" fill="#70232F"/></svg>
            {{ group.members }}
          </span>
          <span class="info-row">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M12 2C6.48 2 2 6.48 2 12C2 17.52 6.48 22 12 22C17.52 22 22 17.52 22 12C22 6.48 17.52 2 12 2ZM12 20C7.59 20 4 16.41 4 12C4 7.59 7.59 4 12 4C16.41 4 20 7.59 20 12C20 16.41 16.41 20 12 20ZM12.5 7H11V12L15.25 14.92L16 13.54L12.5 11.25V7Z" fill="#70232F"/></svg>
            {{ group.duration }}
          </span>
        </div>

        <div class="down">
          <div class="header">РАСПИСАНИЕ ЗАНЯТИЙ</div>
          <span class="subdown">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M20 3H19V1H17V3H7V1H5V3H4C2.9 3 2 3.9 2 5V21C2 22.1 2.9 23 4 23H20C21.1 23 22 22.1 22 21V5C22 3.9 21.1 3 20 3ZM20 21H4V8H20V21ZM20 6H4V5H20V6Z" fill="#70232F"/></svg>
            <span class="date">{{ schedule.days }}</span>
          </span>
          <span class="subdown">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M11.99 2C6.47 2 2 6.48 2 12C2 17.52 6.47 22 11.99 22C17.52 22 22 17.52 22 12C22 6.48 17.52 2 11.99 2ZM12 20C7.58 20 4 16.42 4 12C4 7.58 7.58 4 12 4C16.42 4 20 7.58 20 12C20 16.42 16.42 20 12 20Z" fill="#70232F"/><path d="M12.5 7H11V13L16.25 16.15L17 14.92L12.5 12.25V7Z" fill="#70232F"/></svg>
            <div class="time-slots">
              <span class="time" v-for="(slot, index) in schedule.slots" :key="index">
                {{ slot }}
              </span>
            </div>
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  group: {
    type: Object,
    required: true
  },
  schedule: {
    type: Object,
    required: true
  }
})
</script>

<style scoped>
.card {
  display: flex;
  gap: 16px;
  background: #fff;
  border-radius: 5px;
  padding: 20px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
  align-items: center;
  font-size: 16px;
  border-top: #70232F 3px solid;
  width: 100%;
}
.cards-wrapper {
  width:100%;
  margin: 0 auto;
}
.header{
  font-family: 'Montserrat', sans-serif;
  font-weight: 600;
  font-size: 18px;
  color:#70232F;
}
.subheader{
  font-family: 'Montserrat', sans-serif;
  font-size: 16px;
  color:#333333;
  font-weight: 500;
}
.card-content {
  display: flex;
  flex-direction: row;
  gap: 80px;
  width: 100%;
}
.info-row {
  display:flex;
  gap:10px;
  align-items: center;
  font-family: 'Montserrat', sans-serif;
}
.info-row svg {
  width: 18px;
  height: 18px;
  flex-shrink: 0;
}
.date {
  font-family: 'Montserrat', sans-serif;
  font-weight: 500;
}
.time-slots {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
.time {
  background: #F7DAAB;
  font-family: 'Montserrat', sans-serif;
  font-weight: 400;
  padding: 4px 15px;
  border-radius: 5px;
  color: #333333;
}
.upp{
  display:flex;
  flex-direction: column;
  align-items: flex-start;
  gap:10px;
}
.down{
  display:flex;
  flex-direction: column;
  align-items: flex-start;
  gap:10px;
}
.subdown{
  display:flex;
  align-items: center;
  gap:10px;
}
.subdown svg {
  width: 18px;
  height: 18px;
  flex-shrink: 0;
}
</style>
