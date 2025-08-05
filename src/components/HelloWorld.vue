<script setup>
  import { ref } from 'vue'

  const products = ref([
    { id: '1', title: '珍珠奶茶',description: '香濃奶茶搭配QQ珍珠', price: 50, inventory: 20 },
    { id: '2', title: '冬瓜檸檬',description: '清新冬瓜配上新鮮檸檬', price: 45, inventory: 18 },
    { id: '3', title: '翡翠檸檬',description: '綠茶與檸檬的完美結合', price: 55, inventory: 34 },
    { id: '4', title: '四季春茶',description: '香醇四季春茶，回甘無比', price: 45, inventory: 10 },
    { id: '5', title: '阿薩姆奶茶',description: '阿薩姆紅茶搭配香醇鮮奶', price: 50, inventory: 25 },
    { id: '6', title: '檸檬冰茶',description: '檸檬與冰茶的清新組合', price: 45, inventory: 20 },
    { id: '7', title: '芒果綠茶',description: '芒果與綠茶的獨特風味', price: 55, inventory: 18 },
    { id: '8', title: '抹茶拿鐵',description: '抹茶與鮮奶的絕配', price: 60, inventory: 20 }
  ])

  const productList = ref(products);

  function changeInventoryNum(id , inventory) {

    if (inventory < 0) {
      return; 
    }
    
    productList.value = productList.value.map((item) => {
      if(item.id === id) {
        item.inventory = inventory;
      }
      return item;
    })
  }
</script>

<template>
  <table>
    <thead>
      <tr>
        <th scope="col">品項</th>
        <th scope="col">描述</th>
        <th scope="col">價格</th>
        <th scope="col">庫存</th>
      </tr>
    </thead>
    <tbody>
      <tr 
          v-for="products in productList"
          :key="products.id"
          class="text-black">
        <td>{{ products.title }}</td>
        <td><small>{{ products.description }}</small></td>
        <td>{{ products.price }}</td>
        <td><button v-on:click="changeInventoryNum(products.id, products.inventory - 1)" type="button">-</button>{{ products.inventory }}<button v-on:click="changeInventoryNum(products.id, products.inventory + 1)" type="button">+</button></td>
      </tr>
    </tbody>
  </table>
</template>