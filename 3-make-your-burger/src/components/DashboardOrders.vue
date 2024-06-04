<script setup lang="ts">
import { onMounted, reactive } from 'vue'

interface Order {
  id: number
  name: string
  bread: string
  meat: string
  optionals: string[]
  status: string
}

const orders = reactive<Order[]>([])

onMounted(async () => {
  const req = await fetch('http://localhost:3001/burgers')
  const data: Order[] = await req.json()

  console.log(data)
  orders.push(...data)
})

function deleteOrder(id: number) {}
</script>

<template>
  <div>
    <table class="burger-table">
      <thead>
        <tr class="burger-table-heading">
          <th class="burger-table-id">#:</th>
          <th>Cliente:</th>
          <th>Pão:</th>
          <th>Carne:</th>
          <th>Opcionais:</th>
          <th>Ações:</th>
        </tr>
      </thead>
      <tbody class="burger-table-rows">
        <tr v-for="order in orders" :key="order.id" class="burger-table-row">
          <td class="order-number">{{ order.id }}</td>
          <td>{{ order.name }}</td>
          <td>{{ order.bread }}</td>
          <td>{{ order.meat }}</td>
          <td>{{ "order.optionals.join(', ')" }}</td>
          <td>
            <select name="status" id="status" class="status">
              <option value="">Selecione</option>
            </select>
            <!-- <button @click="editOrder(order.id)">Editar</button> -->
            <button @click="deleteOrder(order.id)" class="delete-btn">Cancelar</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped lang="scss">
.burger-table {
  width: 100%;
  margin: 0 auto;

  .burger-table-heading {
    display: flex;
    text-align: left;
    font-weight: bold;
    padding: 0.75rem;
    border-bottom: 3px solid #333;
    gap: 1rem;

    th {
      width: 100%;

      &.burger-table-id {
        width: 16rem;
      }
    }
  }

  .burger-table-rows {
    display: flex;
    flex-direction: column;

    .burger-table-row {
      display: flex;
      width: 100%;
      padding: 0.75rem;
      border-bottom: 1px solid #ccc;
      gap: 1rem;

      td {
        width: 100%;

        &.order-number {
          width: 16rem;
        }
      }

      .status {
        padding: 0.75rem 0.25rem;
        margin-right: 0.75rem;
      }

      .delete-btn {
        background-color: var(--color-black-soft);
        color: var(--color-primary);
        font-weight: bold;
        border: 2px solid var(--color-black-soft);
        padding: 0.75rem 1rem;
        margin: 0 auto;
        cursor: pointer;
        transition: 0.5s;

        &:hover {
          background-color: transparent;
          color: var(--color-black-soft);
        }
      }
    }
  }
}
</style>
