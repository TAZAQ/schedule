<template>
  <schedule-grid :grid="grid" />
</template>

<script>
import ScheduleGrid from "@/components/Schedule/components/ScheduleGrid.vue"

export default {
  name: "ScheduleRoot",
  components: { ScheduleGrid },
  data() {
    return {
      timeRows1: [
        '9:00',
        '10:00',
        '11:00',
        '12:00',
        '13:00',
        '14:00',
        '15:00',
        '16:00',
        '17:00',
      ],

      timeRows2: [
        '9:00',
        '9:30',
        '10:00',
        '10:30',
        '11:00',
        '11:30',
        '12:00',
        '12:30',
        '13:00',
        '13:30',
        '14:00',
        '14:30',
        '15:00',
        '15:30',
        '16:00',
        '16:30',
        '17:00',
        '17:30',
      ],
    }
  },

  computed: {
    timeRows() {
      return this.timeRows2
    },

    columnsGroups() {
      return [
        {
          groupHeader: '28.08.2022',
          headers: [
            { id: 1, shortName: 'Иванов И.И.' },
            { id: 2, shortName: 'Сергеев С.С.' },
          ],
        },
      ]
    },

    grid() {
      const groupsRow = [
        '',
        ...this.columnsGroups.map((col) => col.groupHeader),
      ]

      const headersRow = [
        '',
        ...this.columnsGroups.map((col) => col.headers ).flat(),
      ]

      const scheduleRows = this.timeRows.map((time) => {
        return [
          time,
          ...headersRow.slice(1).map((header) => ({ id: header.id, time })),
        ]
      })

      return [
        groupsRow,
        headersRow,
        ...scheduleRows,
      ]
    },
  },
}
</script>
