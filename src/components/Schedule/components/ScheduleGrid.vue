<template>
  <div class="schedule-grid">
    <div
      v-for="(row, rowIndex) in grid"
      :key="`row:${rowIndex}`"
      class="schedule-grid__row"
    >
      <div
        v-for="(col, colIndex) in row"
        :key="`col:${colIndex}`"
        class="schedule-grid__column"
      >
        {{ col }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ScheduleGrid",
  props: {
    grid: { type: Array, required: true },
  },
}
</script>
