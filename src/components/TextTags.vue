<template>
  <div class="tag-list">
    <div class="tag-list__body">
      <div
        class="tag-list__row"
        :class="`justify-${validatedAlignment}`"
      >
        <div
          class="tag tag-list__column"
          v-for="(tag, index) in filteredTags"
          :key="index"
        >
          <v-icon
            class="tag__divider"
            v-if="index !== 0"
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

          <span class="tag__text">
            {{ tag.text }}
          </span>
        </div>
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
      return ['center', 'start'].includes(this.alignment) ? this.alignment : 'start';
    },
    filteredTags() {
      return this.tags.filter((tag) => typeof tag === 'object' && 'text' in tag);
    },
  },
};
</script>

<style lang="scss">
.tag-list {
  &__body {
    max-height: 1.5em;
    overflow: hidden;
  }
  &__row {
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
