<template>
  <div class="calender">
    <Calendar />
  </div>
</template>

<script>
import Calendar from "./components/Calendar";
export default {
  name: "App",
  data() {
    return {
      fname: "Urak",
      cname: "Ferraz",
      heroes: [
        {
          name: "Super Man",
        },
        {
          name: "Super Girl",
        },
        {
          name: "Batman",
        },
        {
          name: "Robin",
        },
        {
          name: "Flash",
        },
      ],
      newHero: "",
      mostrar: true,
      isDisabled: false,
    };
  },
  created() {
    console.log(this.heroes);
  },
  computed: {
    herosCount() {
      return this.heroes.length;
    },
    fullname() {
      return this.cname + this.fname;
    },
  },
  methods: {
    enviar() {
      if (this.newHero !== "") {
        this.heroes.push({ name: this.newHero });
        this.newHero = "";
        console.log(this.heroes);
      }
    },
    deltask(index) {
      this.heroes.splice(index, 1);
    },
  },
  components: {
    Calendar,
  },
};
</script>

<style lang="scss">
@import "~bulma";
</style>
