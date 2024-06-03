<template>
  <div class="px-4">
    <h1 class="pb-4 pt-2">Lista de produtos</h1>

    <v-btn color="primary" @click="goToAddProduct">Adicionar Produto</v-btn>

    <v-table height="600px" fixed-header>
      <thead>
        <tr>
          <th>Id</th>
          <th>Nome</th>
          <th>Preço</th>
          <th>Quantidade</th>
          <th>Categoria</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in products" :key="item.id">
          <td>{{ item.id }}</td>
          <td>{{ item.name }}</td>
          <td>R$ {{ item.price }}</td>
          <td>{{ item.quantity }}</td>
          <td>{{ item.category }}</td>
          <td>
            <v-btn color="primary" text @click="editProduct(item.id)"
              >Edit</v-btn
            >
            <v-btn color="error" text @click="removeProduct(item.id)"
              >Delete</v-btn
            >
          </td>
        </tr>
      </tbody>
    </v-table>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import { useRouter } from "vue-router";
import { listProducts } from "@/fakeapi";

const router = useRouter();

const products = ref([]);

onMounted(async () => {
  await populateProducts();
});

const populateProducts = async () => {
  // TODO: Obter produtos via API
  products.value = listProducts();
};

const removeProduct = (id: number) => {
  // TODO: Remover produto via API
  const index = products.value.findIndex((item) => item.id === id);
  if (index !== -1) {
    products.value.splice(index, 1);
  }
};

const editProduct = (id: number) => {
  router.push(`/products/edit/${id}`);
};

const goToAddProduct = () => {
  router.push("/products/add");
};
</script>

<style scoped lang="scss"></style>
