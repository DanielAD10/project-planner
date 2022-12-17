<template>
  <nav class="filter-nav">
      <button @click="filterBy('all')" :class="{active: current === 'all'}">all</button>
      <button @click="filterBy('complete')" :class="{active: current === 'complete'}">complete</button>
      <button @click="filterBy('ongoing')" :class="{active: current === 'ongoing'}">ongoing</button>
  </nav>
</template>

<script>
export default {
    props:['current'],
    methods: {
        filterBy(value) {
            this.$emit("filterValue", value)
        }
    }
}
</script>

<style>
    .filter-nav button {
        display: inline-block;
        background-color: aliceblue;
        color: darkslategrey;
        margin: 0 10px 10px;
        text-transform: uppercase;
        font-size: 14px;
        letter-spacing: 1px;
        font-weight: bold;
    }
    button.active {
        background-color: darkslategrey;
        color: aliceblue;
    }
</style>