<template>
  <div class="tag-list">
    <div
      class="tag-list__row"
      :class="`justify-${validatedAlignment}`"
    >
      <div
        class="tag tag-list__column"
        v-for="(tag, index) in tagsWithDivider"
        :key="index"
      >
        <v-icon
          class="tag__divider"
          v-if="tag.divider"
          :size="dotIconSize"
        >
          mdi-circle
        </v-icon>

        <v-icon
          class="tag__icon"
          v-if="tag.icon"
        >
          {{ tag.icon }}
        </v-icon>

        <span
          class="tag__text"
          v-if="tag.text"
        >
          {{ tag.text }}
        </span>
      </div>
    </div>
</div>
</template>

<script>
export default {
  name: 'TextTags',

  props: {
    tags: {
      type: Array,
      required: true,
    },
    alignment: {
      type: String,
    },
  },

  data: () => ({
    dotIconSize: '0.2em',
  }),

  computed: {
    validatedAlignment() {
      return ['space-between', 'start'].includes(this.alignment) ? this.alignment : 'start';
    },
    tagsWithDivider() {
      const filteredTags = this.filterTags(this.tags);
      return filteredTags.flatMap(
        (item, index) => (index < filteredTags.length - 1 ? [item, { divider: true }] : item),
      );
    },
  },

  methods: {
    filterTags(tags) {
      return tags.filter((tag) => typeof tag === 'object' && 'text' in tag);
    },
  },
};
</script>

<style lang="scss">
.tag-list {
  &__row {
    max-height: 1.5em;
    overflow: hidden;
    display: flex;
    flex-wrap: wrap;
  }
  &__column {
    display: flex;
    align-items: center;
  }
}

.tag {
  &__divider {
    margin: 0 10px;
  }
  &__icon {
    margin-right: 5px;
  }
}
</style>
