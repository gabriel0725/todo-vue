<script setup>
const props = defineProps(['tarefas', 'filtroAtual'])
</script>

<template>
  <ul v-if="props.tarefas.length > 0" class="list-group mt-4">
    <li class="list-group-item" v-for="tarefa in props.tarefas" :key="tarefa.titulo">
      <input @change="evento => tarefa.finalizada = evento.target.checked" type="checkbox" :checked="tarefa.finalizada" :id="tarefa.titulo">
      <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
        {{ tarefa.titulo }}
      </label>
    </li>
  </ul>

  <span v-else-if="props.filtroAtual === 'pendentes'">Você não possui tarefas pendentes</span>
</template>

<style scoped>
.done {
  text-decoration: line-through;
}
</style>