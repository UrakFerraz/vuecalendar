<template>
  <section class="hero is-small is-primary">
    <div class="hero-body">
      <p class="title">Vue Calendar</p>
      <p class="subtitle">{{ currentMonthName }} de {{ currentYear }}</p>
    </div>
  </section>
  <div class="block">
    <div class="container is-max-desktop">
      <section class="calendar-days">
        <p :key="index" v-for="(dia, index) in dias">
          {{ dia }}
        </p>
      </section>
      <section class="calendar-nums">
        <p :key="num" v-for="num in startDay()"></p>
        <p :key="index" v-for="(dia, index) in 31">
          {{ dia }}
        </p>
      </section>
    </div>
  </div>
  <div class="block">
    <div class="prevNext container is-max-desktop buttons">
      <button class="button is-danger is-outlined" @click="prevDay()">
        <span class="icon is-small">
          <i class="fas fa-times"></i>
        </span>
        <span>Prev</span>
      </button>
      <button class="button is-danger is-outlined" @click="nextDay()">
        <span>Next</span>
        <span class="icon is-small">
          <i class="fas fa-times"></i>
        </span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentMonth: new Date().getMonth(),
      currentYear: new Date().getFullYear(),
      dias: [
        "Domingo",
        "Segunda-feira",
        "Terça-feira",
        "Quarta-feira",
        "Quinta-feira",
        "Sexta-feira",
        "Sábado",
      ],
    };
  },
  methods: {
    daysInMonth(year, month) {
      return new Date(year, month, 0).getDate();
    },
    startDay() {
      return new Date(this.currentYear, this.currentMonth, 1).getDay();
    },
    nextDay() {
      if (this.currentMonth === 11) {
        this.currentMonth = 1;
        this.currentYear++;
      } else {
        this.currentMonth++;
      }
    },
    prevDay() {
      if (this.currentMonth < 1) {
        this.currentMonth = 11;
        this.currentYear--;
      } else {
        this.currentMonth--;
      }
    },
  },
  computed: {
    currentMonthName() {
      return new Date(this.currentYear, this.currentMonth).toLocaleString(
        "pt-BR",
        {
          month: "long",
        }
      );
    },
  },
};
</script>

<style lang="sass" scoped>
.hero-body
  p
    text-transform: capitalize

.calendar-days
  display: grid
  grid-template-columns: repeat(7, 1fr)
  gap: 10px
  align-content: center
  justify-content: space-between
  padding: 20px
  background-color: #2e3537

  > p
      color: #f8b064
      text-align: center

.calendar-nums
  display: grid
  grid-template-columns: repeat(7, 1fr)
  gap: 30px
  align-content: center
  justify-content: space-between
  padding: 20px

  > p
    text-align: center
    font-size: 30px

.prevNext
  display: flex
  justify-content: space-between

.block:nth-of-type(2)
  position: absolute
  left: 50%
  transform: translateX(-50%)
  padding: 20px
  bottom: 0
  min-width: 220px

@media (max-width: 700px)
  p
    font-size: 16px !important

  .calendar-days p
    font-size: 10px !important
    align-self: center
    line-height: 1
</style>
