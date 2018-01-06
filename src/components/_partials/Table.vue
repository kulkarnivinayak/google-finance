<template>
  <table class="table">
      <thead>
        <tr>
          <th>Opening Value</th>
          <th>Low Value</th>
          <th>Deviation</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>{{ finance.l }}</td>
          <td>{{ finance.op }}</td>
          <td>{{ finance.cp }}</td>
        </tr>
      </tbody>
    </table>
</template>
<script>
export default {
  name: 'TableData',
  props: ['finance'],
};
</script>

