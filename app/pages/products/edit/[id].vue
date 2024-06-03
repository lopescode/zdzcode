<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>Editar produto</h1>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <v-text-field
          label="Nome"
          v-model="product.name"
          outlined
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <v-text-field
          label="Preço"
          v-model="product.price"
          outlined
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <v-text-field
          label="Quantidade"
          v-model="product.quantity"
          outlined
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <v-text-field
          label="Categoria"
          v-model="product.category"
          outlined
        ></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <v-btn @click="saveProduct" color="primary">Salvar</v-btn>
        <v-btn @click="returnButton" color="error">Cancelar</v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import { useRoute, useRouter } from "vue-router";
import { listProducts } from "@/fakeapi";

const router = useRouter();
const route = useRoute();

const product = ref({
  name: "",
  price: "",
  quantity: "",
  category: "",
});

onMounted(async () => {
  await populateProduct();
});

const populateProduct = async () => {
  // TODO: Obter produto via API
  const productId = Number(route.params.id);
  const products = listProducts();
  const productFetched = products.find((item) => item.id === productId);

  if (productFetched) {
    product.value = { ...productFetched };
  }
};

const saveProduct = () => {
  // TODO: Editar produto via API
  products[productId] = product.value;

  router.push(`/`);
};

const returnButton = () => {
  router.push(`/`);
};
</script>

<style scoped lang="scss">
.v-container {
  max-width: 600px;
  margin: 0 auto;
}
</style>
