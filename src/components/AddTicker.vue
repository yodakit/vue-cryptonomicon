<template>
  <section>
    <div class="flex">
      <div class="max-w-xs">
        <label for="wallet" class="block text-sm font-medium text-gray-700"
          >Тикер</label
        >
        <div class="mt-1 relative rounded-md shadow-md">
          <input
            v-model="ticker"
            @keydown.enter="add"
            type="text"
            name="wallet"
            id="wallet"
            class="block w-full pr-10 border-gray-300 text-gray-900 focus:outline-none focus:ring-gray-500 focus:border-gray-500 sm:text-sm rounded-md"
            placeholder="Например DOGE"
          />
        </div>
      </div>
    </div>
    <add-button @click="add" />
  </section>
</template>

<script>
import AddButton from "./AddButton.vue";
export default {
  components: {
    AddButton,
  },
  data() {
    return {
      ticker: "",
      currentTicker: {},
    };
  },
  methods: {
    add() {
      this.currentTicker = {
        name: this.ticker,
        price: "-",
      };
      this.ticker = "";
      this.filter = "";
      this.$emit("add-ticker", this.currentTicker);
    },
  },
};
</script>
