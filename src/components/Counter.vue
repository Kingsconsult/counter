<template>
  <!-- <div> -->
    <div v-if="loaded">
    <section
      class="text-3xl flex justify-center content-center flex-col mx-auto text-center"
    >
    <h5 v-if="!expired">Hello kings counter</h5>
    <h5 v-else>Hello  counter</h5>
      
    </section>

    <section class="flex text-6xl flex justify-center content-center">
      <div class="days mr-2 relative">
        {{ displayDays }}
        <div class="label text-sm absolute button-0">days</div>
      </div>
      <span class="leading-snug">:</span>
      <div class="hours mr-2 relative">
        {{ displayHours }}
        <div class="label text-sm absolute button-0">hours</div>
      </div>
      <span class="leading-snug">:</span>
      <div class="minutes mr-2 relative">
        {{ displayMinutes }}
        <div class="label text-sm absolute button-0">minutes</div>
      </div>
      <span class="leading-snug">:</span>
      <div class="seconds mr-2 relative">
        <div>{{ displaySeconds }}</div>
        <div class="label text-sm absolute button-0">seconds</div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  props: ["year", "month", "date", "hour", "minute", "second", "millisecond"],
  data: () => ({
    displayDays: 0,
    displayHours: 0,
    displayMinutes: 0,
    displaySeconds: 0,
    loaded: false,
    expired: false
  }),
  computed: {
    _seconds: () => 1000,
    _minutes() {
      return this._seconds * 60;
    },
    _hours() {
      return this._minutes * 60;
    },
    _days() {
      return this._hours * 24;
    },
    end() {
      return new Date(
        this.year,
        this.month,
        this.date,
        this.hour,
        this.minute,
        this.second,
        this.millisecond
      );
    },
  },
  mounted() {
    this.showRemaining();
  },
  methods: {
    formatNum: (num) => (num < 10 ? "0" + num : num),

    showRemaining() {
      const timer = setInterval(() => {
        const now = new Date();
        // const end = new Date(2021, 0, 0, 0, 0, 0, 0);
        const distance = this.end.getTime() - now.getTime();

        if (distance < 0) {
          clearInterval(timer);
          this.expired = true;
          this.loaded = true;
          return;
        }

        const days = Math.floor(distance / this._days);
        const hours = Math.floor((distance % this._days) / this._hours);
        const minutes = Math.floor((distance % this._hours) / this._minutes);
        const seconds = Math.floor((distance % this._minutes) / this._seconds);

        this.displayMinutes = this.formatNum(minutes);
        this.displaySeconds = this.formatNum(seconds);
        this.displayHours = this.formatNum(hours);
        this.displayDays = this.formatNum(days);
        this.loaded = true;
      }, 1000);
    },
  },
};
</script>

<style scoped>
.seconds {
  max-width: 60px;
}
</style>