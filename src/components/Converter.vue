<script setup>
import { ref, watch } from 'vue';

const divisaUno = ref('Euro');
const divisaDos = ref('Dolar');
const parteUno = ref(0);
const parteDos = ref(0);
const rateText = ref('');

const tasasCambio = {
  "Euro": {
    "Dolar": 1.1,
    "Yen": 129.53,
    "Lempira": 27.15
  },
  "Dolar": {
    "Euro": 0.91,
    "Yen": 117.75,
    "Lempira": 24.67
  },
  "Yen": {
    "Euro": 0.0077,
    "Dolar": 0.0085,
    "Lempira": 0.21
  },
  "Lempira": {
    "Euro": 0.037,
    "Dolar": 0.041,
    "Yen": 4.75
  }
};

const calcular = () => {
  const tasa = tasasCambio[divisaUno.value][divisaDos.value];
  parteDos.value = (parteUno.value * tasa).toFixed(2);
  rateText.value = `1 ${divisaUno.value} = ${tasa} ${divisaDos.value}`;
};

watch([divisaUno, divisaDos, parteUno], calcular);

const invertirDivisas = () => {
  const tempDivisa = divisaUno.value;
  divisaUno.value = divisaDos.value;
  divisaDos.value = tempDivisa;
  calcular();
};

calcular();
</script>

<template>
    <div class="cabecera">
      <h1>Conversor de divisas</h1>
      <p>Escoge los tipos de moneda y la cantidad para la conversión</p>
    </div>
    <div class="conversor">
      <div class="cantidad_uno">
        <select v-model="divisaUno">
          <option value="Euro">Euro (€)</option>
          <option value="Dolar">Dolar ($)</option>
          <option value="Yen">Yen (¥)</option>
          <option value="Lempira">Lempira Hondureño (Honduras)</option>
        </select>
        <input type="number" v-model.number="parteUno" placeholder="0" />
      </div>
  
      <div class="invertir">
        <button class="boton" @click="invertirDivisas">Invertir</button>
        <div class="rate">{{ rateText }}</div>
      </div>
  
      <div class="cantidad_dos">
        <select v-model="divisaDos">
          <option value="Dolar">Dolar ($)</option>
          <option value="Euro">Euro (€)</option>
          <option value="Yen">Yen (¥)</option>
          <option value="Lempira">Lempira Hondureño (Honduras)</option>
        </select>
        <input type="number" :value="parteDos" placeholder="0" readonly />
      </div>
    </div>
  </template>
  
<style scoped lang="scss">
.cabecera {
  text-align: center;
  margin-bottom: 20px;
}

.conversor {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.cantidad_uno, .cantidad_dos {
  margin-bottom: 10px;
}

.invertir {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 10px;
}

.boton {
  margin-bottom: 10px;
}

.rate {
  font-weight: bold;
}
</style>