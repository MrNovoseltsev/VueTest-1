<script>
import initialData from './data/data.json';
import TempTable from './components/TempTable.vue';

export default {
  data() {
    return {initialData};
  },
  components: {TempTable},
  methods: {
    changeValue(name, newValue) {
      this.initialData.find(item => item.name == name).value = newValue;
    }
  }
}
</script>

<template>
    <TempTable :data="initialData" @change="changeValue"/>
</template>
