<script lang="ts">
import { ref } from "vue";

export default{
  name: 'ProductsListView',
  props: {
    products: {
      type: Array as () => { id: number; label: string; description: string; quantity: number }[],
    },
  },
  setup(props) {
    const productsData = props.products;
    console.log(productsData)
    return {
      productsData
    };
  }
}
</script>
<template>
  <div>
    <table>
      <thead>
    <tr>
      <th>ID</th>
      <th>Label</th>
      <th>Description</th>
      <th>Statut</th>
    </tr>
  </thead>
  <tbody>
     <tr v-for="(productData, i) in productsData" :key="i">
      <td>{{ productData.id }}</td>
      <td>{{ productData.label }}</td>
      <td>{{ productData.description }}</td>
      <td v-if="productData.quantity > 0"> Disponible</td>
      <td v-if="productData.quantity < 1"> Indisponible</td>
    </tr>
  </tbody>
    </table>
  </div>
</template>
<style></style>
