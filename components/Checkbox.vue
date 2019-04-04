<template>
  <label class="checkbox" :class="theme">
    <input v-model="value" type="checkbox" />
    <div class="checkmark" :class="{'selected': value}">
      <svg v-if="value" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 230 200"><path d="M20 130l40 40L200 30" stroke-width="25" fill="none"/></svg>
    </div>
    <slot />
  </label>
</template>

<script>
export default {
  props: ["value", "theme"],
  watch: {
    value: function(value){
      this.$emit('input', value);
    }
  }
};
</script>

<style lang="scss" scoped>
@import "~/assets/scss/styles.scss";

.checkbox {
  display: flex;
  user-select: none;

  input {
    display: none;
  }

  .checkmark {
    display: inline-block;
    width: 0.9em;
    height: 0.9em;
    border-radius: 2px;
    margin-right: 5px;
    padding: 2px;

    svg {
      display: block;
    }
  }


  /* news theme*/
  &.news {
    .checkmark {
      border: 2px solid #000;
      svg {
        stroke: #fff;
      }
      &.selected {
        background-color: $color-blue;
        border: none;
      }
    }
    &:hover {
      .checkmark {
        background-color: $color-blue;
        border: none;
      }
    }
  }

  /* white theme*/
  &.white {
    .checkmark {
      border: 2px solid #FFF;
      svg {
        stroke: #000;
      }
      &.selected {
        background-color: #FFF;
        border: none;
      }
    }
    &:hover {
      .checkmark {
        background-color: #FFF;
        border: none;
      }
    }
  }
}
</style>
