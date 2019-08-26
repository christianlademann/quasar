<template>
  <div class="q-pa-md" style="max-width: 350px">
    <q-list bordered separator>

      <q-slide-item @top="onTop" @bottom="onBottom">
        <template v-slot:top>
          <q-icon name="done" />
        </template>

        <template v-slot:bottom>
          <q-icon name="note" />
        </template>

        <q-item>
          <q-item-section avatar>
            <q-avatar>
              <img src="https://cdn.quasar.dev/img/avatar2.jpg">
            </q-avatar>
          </q-item-section>
          <q-item-section>Top and bottom actions</q-item-section>
        </q-item>
      </q-slide-item>

      <q-slide-item @top="onTop" @bottom="onBottom" @left="onLeft" @right="onRight">
        <template v-slot:top>
          <q-icon name="pause" />
        </template>

        <template v-slot:bottom>
          <q-icon name="play_arrow" />
        </template>

        <template v-slot:left>
          <q-icon name="skip_previous" />
        </template>

        <template v-slot:right>
          <q-icon name="skip_next" />
        </template>

        <q-item>
          <q-item-section avatar>
            <q-avatar>
              <img src="https://cdn.quasar.dev/img/avatar2.jpg">
            </q-avatar>
          </q-item-section>
          <q-item-section>All actions</q-item-section>
        </q-item>
      </q-slide-item>

    </q-list>
  </div>
</template>

<script>
export default {
  methods: {
    onLeft ({ reset }) {
      this.$q.notify('Left action triggered. Resetting in 1 second.')
      this.finalize(reset)
    },

    onRight ({ reset }) {
      this.$q.notify('Right action triggered. Resetting in 1 second.')
      this.finalize(reset)
    },

    onTop ({ reset }) {
      this.$q.notify('Top action triggered. Resetting in 1 second.')
      this.finalize(reset)
    },

    onBottom ({ reset }) {
      this.$q.notify('Bottom action triggered. Resetting in 1 second.')
      this.finalize(reset)
    },

    finalize (reset) {
      this.timer = setTimeout(() => {
        reset()
      }, 1000)
    }
  },

  beforeDestroy () {
    clearTimeout(this.timer)
  }
}
</script>
