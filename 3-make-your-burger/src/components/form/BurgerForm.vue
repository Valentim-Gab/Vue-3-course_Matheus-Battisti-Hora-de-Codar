<script setup lang="ts"></script>

<template>
  <section>
    <p>Componente de Mensagem</p>
    <div>
      <form action="" id="burger-form">
        <div class="input-container">
          <label for="name">Nome do cliente:</label>
          <input type="text" id="name" name="name" v-model="name" placeholder="Digite o seu nome" />
        </div>
        <div class="input-container">
          <label for="bread">Escolha o pão:</label>
          <select type="text" id="bread" name="bread" v-model="bread">
            <option value="">Selecione o seu pão</option>
            <option value="integral">Integral</option>
            <option value="branco">Branco</option>
            <option value="australiano">Australiano</option>
          </select>
        </div>
        <div class="input-container">
          <label for="meat">Escolha a carne do seu burger:</label>
          <select type="text" id="meat" name="meat" v-model="meat">
            <option value="">Selecione o tipo de carne</option>
            <option value="maminha">Maminha</option>
          </select>
        </div>
        <div id="optionals-container" class="input-container">
          <label id="optionals-title" for="optionals">Selecione os opcionais:</label>
          <div class="checkbox-container">
            <input
              type="checkbox"
              name="optionals"
              id="optionals"
              v-model="optionals"
              value="salame"
            />
            <span>Salame</span>
          </div>
          <div class="checkbox-container">
            <input
              type="checkbox"
              name="optionals"
              id="optionals"
              v-model="optionals"
              value="salame"
            />
            <span>Salame</span>
          </div>
          <div class="checkbox-container">
            <input
              type="checkbox"
              name="optionals"
              id="optionals"
              v-model="optionals"
              value="salame"
            />
            <span>Salame</span>
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

        span,
        input {
          width: auto;
        }

        span {
          margin-left: 0.5rem;
          font-weight: bold;
        }
      }
    }

    label {
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
