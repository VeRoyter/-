<template>
  <div class="event-card">
    <div class="card-content">
      <div class="card-image">
        <NuxtImg 
          src="/images/sport-icon.svg" 
          width="200"
          height="200"
          alt="Тяжелая атлетика"
        />
      </div>
      
      <div class="card-details">
        <div class="card-header">
          <h3 class="event-title">Тяжелая атлетика (в Юбилейном мкр.)</h3>
          <div class="tag free-tag">
            <span>Бесплатно</span>
          </div>
        </div>
        
        <div class="event-info">
          <div class="info-item hashtag">#Тяжелая атлетика</div>
          
          <div class="info-row">
            <div class="icon age-icon"></div>
            <span>10-18 лет</span>
          </div>
          
          <div class="info-row">
            <div class="icon location-icon"></div>
            <span>г. Иркутск, Юбилейный мкр., стр. 49/1</span>
          </div>
          
          <div class="info-row">
            <div class="icon building-icon"></div>
            <span>ФОК "Юбилейный"</span>
          </div>
          
          <div class="schedule">
            <div class="schedule-header">
              <div class="icon clock-icon"></div>
              <div class="days">Пн, Ср, Пт</div>
            </div>
            
            <div class="time-slots">
              <div class="time-slot">09:00 - 10:30</div>
              <div class="time-slot">12:00 - 13:30</div>
              <div class="time-slot">18:00 - 19:30</div>
            </div>
          </div>
        </div>
      </div>
      
      <div class="card-action">
        <button class="details-btn">Подробнее</button>
      </div>
    </div>
  </div>
</template>

<script setup>
// Логика компонента (при необходимости)
</script>

<style scoped>
.event-card {
  /* Основной контейнер карточки */
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  padding: 20px;
  gap: 10px;
  
  width: 1030px;
  min-height: 240px;
  
  background: #FFFFFF;
  border-top: 2px solid #70232F;
  border-radius: 5px;
  position: relative;
}

.card-content {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  padding: 0px;
  gap: 10px;
  width: 100%;
}

.card-image {
  width: 200px;
  height: 200px;
  flex-shrink: 0;
  background: #F0F0F0;
  border-radius: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.card-details {
  display: flex;
  flex-direction: column;
  padding: 0px;
  gap: 10px;
  flex: 1;
}

.card-header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-start;
  width: 100%;
}

.event-title {
  width: 194px;
  height: 40px;
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: 600;
  font-size: 16px;
  line-height: 20px;
  color: #333333;
  margin: 0;
}

.tag {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 5px 15px;
  gap: 10px;
  border-radius: 5px;
}

.free-tag {
  background: #D86B79;
  width: 98px;
  height: 25px;
}

.free-tag span {
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: 500;
  font-size: 12px;
  line-height: 15px;
  color: #FFFFFF;
  width: 68px;
  height: 15px;
}

.event-info {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.hashtag {
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 17px;
  color: #D86B79;
  width: 139px;
  height: 17px;
}

.info-row {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
  height: 20px;
}

.icon {
  width: 18px;
  height: 18px;
  flex-shrink: 0;
}

.age-icon {
  position: relative;
}

.age-icon::before {
  content: "";
  position: absolute;
  width: 18px;
  height: 16px;
  left: 0;
  top: 1px;
  background: #70232F;
  clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
}

.location-icon {
  position: relative;
}

.location-icon::before {
  content: "";
  position: absolute;
  width: 12px;
  height: 16px;
  left: 3px;
  top: 1px;
  background: #70232F;
  clip-path: polygon(50% 0%, 100% 50%, 50% 100%, 0% 50%);
}

.building-icon {
  position: relative;
}

.building-icon::before {
  content: "";
  position: absolute;
  width: 14px;
  height: 14px;
  left: 2px;
  top: 2px;
  background: #70232F;
  border: 1px solid #70232F;
}

.info-row span {
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 20px;
  color: #333333;
}

.schedule {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-top: 5px;
}

.schedule-header {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
}

.clock-icon {
  position: relative;
}

.clock-icon::before {
  content: "";
  position: absolute;
  width: 14px;
  height: 14px;
  left: 2px;
  top: 2px;
  border: 2px solid #70232F;
  border-radius: 50%;
}

.clock-icon::after {
  content: "";
  position: absolute;
  width: 4px;
  height: 4px;
  background: #70232F;
  left: 5px;
  top: 5px;
  border-radius: 50%;
}

.days {
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: 500;
  font-size: 16px;
  line-height: 20px;
  color: #333333;
}

.time-slots {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  gap: 10px;
}

.time-slot {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 4px 10px;
  gap: 10px;
  background: #F7DAAB;
  border-radius: 5px;
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 20px;
  color: #333333;
  height: 28px;
}

.card-action {
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
  align-items: flex-end;
  padding: 10px 20px;
  gap: 10px;
  width: 125px;
  height: 37px;
}

.details-btn {
  width: 85px;
  height: 37px;
  background: #70232F;
  border-radius: 5px;
  border: none;
  font-family: 'Montserrat', sans-serif;
  font-style: normal;
  font-weight: 500;
  font-size: 14px;
  line-height: 17px;
  color: #FFFFFF;
  cursor: pointer;
  transition: background 0.3s;
}

.details-btn:hover {
  background: #5a1c25;
}

/* Адаптивность */
@media (max-width: 1100px) {
  .event-card {
    width: 100%;
  }
  
  .card-content {
    flex-wrap: wrap;
  }
  
  .card-image {
    width: 100%;
    height: 200px;
  }
}

@media (max-width: 768px) {
  .event-card {
    padding: 15px;
  }
  
  .card-header {
    flex-direction: column;
    gap: 10px;
  }
  
  .event-title {
    height: auto;
  }
  
  .time-slots {
    flex-direction: column;
  }
  
  .time-slot {
    width: 100%;
  }
}
</style>