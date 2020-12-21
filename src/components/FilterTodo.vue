<template>
  <div>
    Filter Todos :
    <select @change="limitedTodos($event)">
      <option :key="i" v-for="i in 200">
        {{ i }}
      </option>
    </select>
  </div>
</template>

<script>
import { mapActions } from "vuex";
export default {
  name: "FilterTOdo",
  methods: {
    ...mapActions(["limitedTodos"])
  }
};
</script>

<style>
select {
  margin-top: 20px;
  padding: 6px;
  border: #41b883 1px solid;
}
</style>
