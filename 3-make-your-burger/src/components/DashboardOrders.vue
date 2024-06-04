<script setup lang="ts">
import { onMounted, ref } from 'vue'
import MessageAlert from './MessageAlert.vue'

interface Order {
  id: number
  name: string
  bread: string
  meat: string
  optionals: string[]
  status: string
}

interface Status {
  id: number
  tipo: string
}

const orders = ref<Order[]>([])
const statusList = ref<Status[]>([])
const msg = ref<string | null>(null)

async function fetchOrders() {
  try {
    const req = await fetch('http://localhost:3001/burgers')

    if (!req.ok) {
      throw new Error(`HTTP error! status: ${req.status}`)
    }

    const data: Order[] = await req.json()
    orders.value = data
  } catch (error) {
    console.error('Failed to fetch orders:', error)
  }
}

async function fetchStatuses() {
  try {
    const req = await fetch('http://localhost:3001/status')

    if (!req.ok) {
      throw new Error(`HTTP error! status: ${req.status}`)
    }

    const statusData: Status[] = await req.json()
    statusList.value = statusData
  } catch (error) {
    console.error('Failed to fetch statuses:', error)
  }
}

onMounted(() => {
  fetchOrders()
  fetchStatuses()
})

async function deleteOrder(id: number) {
  try {
    const req = await fetch(`http://localhost:3001/burgers/${id}`, {
      method: 'DELETE'
    })

    if (!req.ok) {
      throw new Error(`HTTP error! status: ${req.status}`)
    }

    const res = await req.json()
    // msg.value = `Pedido Nº ${res.id} cancelado com sucesso!`

    // setTimeout(() => {
    //   msg.value = null
    // }, 3000)

    orders.value = orders.value.filter((order) => order.id !== id)
    // fetchOrders()
  } catch (error) {
    console.error('Failed to delete order:', error)
  }
}

async function updateStatusOrder(e: Event, id: number) {
  const option = e.target as HTMLOptionElement
  const dataJson = JSON.stringify({ status: option.value })

  try {
    const req = await fetch(`http://localhost:3001/burgers/${id}`, {
      method: 'PATCH',
      headers: {
        'Content-Type': 'application/json'
      },
      body: dataJson
    })

    if (!req.ok) {
      throw new Error(`HTTP error! status: ${req.status}`)
    }

    const res = await req.json()
    // msg.value = `Pedido Nº ${res.id} foi atualizado com sucesso!`

    // setTimeout(() => {
    //   msg.value = null
    // }, 3000)
  } catch (error) {
    console.error('Failed to update order:', error)
  }
}
</script>

<template>
  <div>
    <MessageAlert :msg="msg" v-show="msg" />
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
          <td>
            <ul class="optionals-list">
              <li v-for="(optional, index) in order.optionals" :key="index">
                {{ optional }}
              </li>
            </ul>
          </td>
          <td class="actions">
            <select
              name="status"
              id="status"
              class="status"
              @change="updateStatusOrder($event, order.id)"
            >
              <option value="">Selecione</option>
              <option
                v-for="status in statusList"
                :key="status.id"
                :value="status.tipo"
                :selected="order.status == status.tipo"
              >
                {{ status.tipo }}
              </option>
            </select>
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
      }

      .delete-btn {
        background-color: var(--color-black-soft);
        color: var(--color-primary);
        font-weight: bold;
        border: 2px solid var(--color-black-soft);
        padding: 0.75rem 1rem;
        cursor: pointer;
        transition: 0.5s;

        &:hover {
          background-color: transparent;
          color: var(--color-black-soft);
        }
      }

      .optionals-list {
        margin-left: 1.25rem;
      }

      .actions {
        display: flex;
        align-items: center;
        justify-content: flex-start;
        gap: 1rem;
      }
    }
  }
}
</style>
