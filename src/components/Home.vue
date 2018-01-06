<template>
  <div class="container">
    <div class="field">
      <label class="label">Search</label>
      <div class="control">
        <input class="input" type="text" placeholder="Search for Option" v-model="option">
      </div>
    </div>
    <div class="field">
      <div class="control">
        <button class="button is-primary" @click.prevent="loadData" v-if="option">
          Search for {{option}}
        </button>
      </div>
    </div>
    <h1> {{ finance_data.symbol }} </h1>
    <finance-table :finance="finance_data"></finance-table>
  </div>
</template>

<script>
import axios from 'axios';
import FinanceTable from '../components/_partials/Table';

export default {
  name: 'Home',
  components: {
    FinanceTable,
  },
  data() {
    return {
      error: {},
      option: 'SENSEX',
      finance_data: null,
    };
  },
  created() {
    this.loadData();
  },
  methods: {
    loadData() {
      const t = this;
      axios
        .get(`https://finance.google.com/finance?q=${t.option}&output=json`)
        .then((response) => {
          t.finance_data = JSON.parse(JSON.stringify(response.data));
          // const parsedJson = t.sensex
          //   .replace(/\r/g, '')
          //   .replace(/" /g, '')
          //   .replace(/\n/g, '')
          //   .replace(/\\"/g, '')
          //   .replace(/\/\//g, '')
          //   .replace(/\/"/g, '');
          // console.log('parsedJson', parsedJson);
          // t.parsed = parsedJson;
        })
        .catch((error) => {
          t.error = error.data;
        });
    },
  },
};
</script>