<template>
  <v-app>
    <v-main>
      <div class="purple">
        <TextTags :tags="tagList" :alignment="'space-between'" />
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
</style>
