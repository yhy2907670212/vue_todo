<template>
   <div class="filters">
          <!-- <span class="filter active">全部</span> -->
          <span class="filter" v-for="filter in filters" :key="filter.value" @click="$emit('change-filter', filter.value)" :class="{active: selected === filter.value}">
              {{filter.label}}
          </span>
   </div>
</template>

<script>
export default {
    name: 'filterTodo',
    props: ["selected"],
    setup() {
        const filters = [
            {label: "全部",value: "all"},
            {label: "已完成",value: "done"},
            {label: "未完成",value: "todo"}
        ];
        return {
            filters
        }
    }
}
</script>

<style>
.filters {
  display: flex;
  margin: 24px 2px;
  color: #c0c2ce;
  font-size: 14px;
  cursor: pointer;
}
.filters .filter {
  margin-right: 14px;
  transition: 0.8s;
}
.filters .filter.active {
  color: #6b729c;
  transform: scale(1.2);
}
</style>