<template>
  <v-app>
    <v-main>
      <div class="purple">
        <TextTags :tags="tagList" :alignment="'center'" />
      </div>

      <v-divider></v-divider>

      <div class="purple">
        <TextTags :tags="tagList" :alignment="'start'" />
      </div>

      <v-divider></v-divider>

      <div class="purple row_width_200">
        <TextTags :tags="tagList" :alignment="'start'" />
      </div>

      <v-divider></v-divider>

      <div class="purple row_width_300">
        <TextTags :tags="tagList" :alignment="'start'" />
      </div>

      <v-divider></v-divider>

      <div class="purple row_width_400">
        <TextTags :tags="tagList" :alignment="'start'" />
      </div>

    </v-main>
  </v-app>
</template>

<script>
import TextTags from '@/components/TextTags.vue';

export default {
  name: 'App',

  components: {
    TextTags,
  },

  data: () => ({
    tagList: [
      {
        text: '4,3',
        icon: 'mdi-star-outline',
      },
      {
        text: 'Фридландские ворота',
      },
      {
        text: '1,2 км от вас',
      },
    ],
  }),
};
</script>

<style lang="scss">
$black-color: black !important;

.v-icon {
  color: $black-color
}

.row_width_200 {
  width: 200px;
}

.row_width_300 {
  width: 300px;
}

.row_width_400 {
  width: 400px;
}
</style>
