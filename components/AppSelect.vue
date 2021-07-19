<template>
  <div>
    <label for="select">What a {{ select }} do you want?</label>

    <select
      id="select"
      :name="select"
      @change="$emit('change', $event.target.value)"
    >
      <option value>--Please select--</option>
      <option v-for="option in selectOptions" :key="option" :value="option">
        {{ option }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    select: {
      type: String,
      default: "restaurant"
    },
    selectOptions: {
      type: Array,
      default: () => ["tacos", "pizza", "dim sum"]
    }
  }
};
</script>

<style lang="scss" scoped></style>
