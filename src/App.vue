<template>
  <div class="container grid-lg">
    <input v-model="quotes.test" />
    <h1>{{ quotes }}</h1>
  </div>
</template>

<script>
  import { onMounted, reactive, toRefs } from "vue";
  import api from "@/services/api";
  export default {
    name: "App",

    setup() {
      const data = reactive({
        quotes: {
          test: "",
        },
      });

      onMounted(async () => {
        const response = await api.all();
        data.quotes = response.data;
      });

      return { ...toRefs(data) };
    },
  };
</script>
