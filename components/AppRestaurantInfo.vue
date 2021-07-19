<template>
  <section class="restaurantinfo">
    <div v-for="store in datasource" :key="store.id">
      <h2 v-text="store.name" />
      <p>Delivery Time {{ store.deliveryTime }}</p>
      <p>Rating {{ store.rating }}</p>
      <p v-if="store.freeDelivery" class="label">
        <span>Free Delivery</span>
      </p>

      <div class="row">
        <div
          v-for="menuitem in store.menu"
          :key="menuitem.id"
          class="items"
          :style="`background: url(/${menuitem.img}) no-repeat center center`"
        >
          <div class="iteminfo">
            <div>
              <h4 v-text="menuitem.item" />
              <p>{{ priceFormatting(menuitem.price) }}</p>
            </div>
            <nuxt-link :to="`/items/${menuitem.id}`">
              <button class="ghost">View Item</button>
            </nuxt-link>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    // eslint-disable-next-line vue/require-default-prop
    datasource: {
      type: [Array, Object]
    }
  },
  methods: {
    priceFormatting(item) {
      return "$" + item.toFixed(2);
    }
  }
};
</script>

<style lang="scss" scoped></style>
