<script setup lang="ts">
import { onMounted, reactive, ref } from 'vue'
import MessageAlert from '../MessageAlert.vue'

interface Bread {
  id: number
  tipo: string
}

interface Meat {
  id: number
  tipo: string
}

interface Optional {
  id: number
  tipo: string
}

const breads = ref<Bread[]>([])
const meats = ref<Meat[]>([])
const optionalsData = ref<Optional[]>([])
const msg = ref<string | null>(null)

const form = reactive({
  name: '',
  bread: '',
  meat: '',
  optionals: [],
  status: 'Solicitado'
})

onMounted(async () => {
  const req = await fetch('http://localhost:3001/ingredientes')
  const data = await req.json()

  breads.value = data.paes
  meats.value = data.carnes
  optionalsData.value = data.opcionais
})

async function createBurger(e: Event) {
  e.preventDefault()

  const dataJson = JSON.stringify(form)
  const req = await fetch('http://localhost:3001/burgers', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json'
    },
    body: dataJson
  })
  const res = await req.json()

  msg.value = `Pedido Nº ${res.id} realizado com sucesso`

  setTimeout(() => {
    msg.value = null
  }, 3000)

  form.bread = ''
  form.meat = ''
  form.optionals = []
  form.name = ''
}
</script>

<template>
  <section>
    <MessageAlert :msg="msg" v-show="msg" />
    <div>
      <form id="burger-form" @submit="createBurger">
        <div class="input-container">
          <label class="label-input-text" for="name">Nome do cliente:</label>
          <input
            type="text"
            id="name"
            name="name"
            v-model="form.name"
            placeholder="Digite o seu nome"
          />
        </div>
        <div class="input-container">
          <label class="label-input-text" for="bread">Escolha o pão:</label>
          <select id="bread" name="bread" v-model="form.bread">
            <option value="">Selecione o seu pão</option>
            <option v-for="breadItem in breads" :key="breadItem.id" :value="breadItem.tipo">
              {{ breadItem.tipo }}
            </option>
          </select>
        </div>
        <div class="input-container">
          <label class="label-input-text" for="meat">Escolha a carne do seu burger:</label>
          <select id="meat" name="meat" v-model="form.meat">
            <option value="">Selecione o tipo de carne</option>
            <option v-for="meatItem in meats" :key="meatItem.id" :value="meatItem.tipo">
              {{ meatItem.tipo }}
            </option>
          </select>
        </div>
        <div id="optionals-container" class="input-container">
          <label class="label-input-text" id="optionals-title" for="optionals"
            >Selecione os opcionais:</label
          >
          <div
            class="checkbox-container"
            v-for="optionalItem in optionalsData"
            :key="optionalItem.id"
          >
            <input
              type="checkbox"
              :name="optionalItem.id.toString()"
              :id="optionalItem.id.toString()"
              v-model="form.optionals"
              :value="optionalItem.tipo"
            />
            <label class="label-input-checkbox" :for="optionalItem.id.toString()">{{
              optionalItem.tipo
            }}</label>
          </div>
        </div>
        <div class="input-container">
          <button type="submit" class="submit-btn">Criar meu Burger!</button>
        </div>
      </form>
    </div>
  </section>
</template>

<style scoped lang="scss">
#burger-form {
  max-width: 400px;
  margin: 0 auto;

  .input-container {
    display: flex;
    flex-direction: column;
    margin-bottom: 1.25rem;

    &#optionals-container {
      display: flex;
      flex-direction: row;
      flex-wrap: wrap;

      .checkbox-container {
        display: flex;
        align-items: flex-start;
        width: 50%;
        margin-bottom: 1.25rem;

        .label-input-checkbox,
        input {
          width: auto;
          cursor: pointer;
        }

        .label-input-checkbox {
          margin-left: 0.5rem;
          font-weight: bold;
        }
      }
    }

    .label-input-text {
      font-weight: bold;
      margin-bottom: 0.75rem;
      color: var(--color-black-soft);
      padding: 0.5rem 0.75rem;
      border-left: 4px solid var(--color-primary);

      &#optionals-title {
        width: 100%;
      }
    }

    input,
    select,
    .submit-btn {
      padding: 0.5rem 0.75rem;
      width: 100%;
    }

    .submit-btn {
      background-color: var(--color-black-soft);
      color: var(--color-primary);
      font-weight: bold;
      border: 2px solid var(--color-black-soft);
      padding: 0.75rem;
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
</style>
