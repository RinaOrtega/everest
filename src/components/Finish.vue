<template>
  <v-card width="500px">
    <v-card-title
      class="
        display-1
        d-flex
        justify-center
      "
      v-text="title"
    />

    <player-stats
      values
      class="
        justify-space-around
        pa-3
      "
    />

    <lazy-image :src="image" />

    <v-card-text
      class="
        subtitle-1
        text-center
        font-weight-light
      "
      v-html="description"
    />

    <v-card-actions
      class="
        d-flex
        flex-column
        pa-3
      "
    >
      <v-btn
        block
        color="pink"
        @click="startNewGame"
        v-text="'Сыграть ещё раз'"
      />
    </v-card-actions>
  </v-card>
</template>

<script>
  import { mapState, mapActions } from 'vuex'
  import LazyImage from './LazyImage.vue'
  import PlayerStats from './PlayerStats.vue'

  export default {
    name: 'Finish',
    components: {
      LazyImage,
      PlayerStats,
    },
    computed: {
      ...mapState({
        stage: s => s.game.finish,
      }),
      title: vm => vm.stage.title,
      description: vm => vm.stage.description,
      image: vm => vm.stage.image,
    },
    methods: {
      ...mapActions([
        'startNewGame',
      ]),
    },
  }
</script>
