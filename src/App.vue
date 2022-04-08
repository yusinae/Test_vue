<template>
  <h1>ToDo 심플앱</h1>

	<form @submit.prevent="addTodo()">
		<input
			v-model="newTodo"
			name="newTodo"
			autocomplete="off"
		>
		<button>Todo 추가</button>
	</form>

  <br><hr>

	<h2>ToDo목록</h2>
	<ul>
		<li
			v-for="(todo, index) in todos"
			:key="index"
		>
			<span
				:class="{ done: todo.done }"
				@click="doneTodo(todo)"
			>{{ todo.content }}</span>
			<button @click="removeTodo(index)">제거</button>
		</li>
	</ul>

	<h4 v-if="todos.length === 0">목록없음</h4>
</template>

<script>
  import { ref, onBeforeMount } from 'vue';

	export default {
		name: 'App',
    
		setup () {
			const newTodo = ref(''); //변경될 값
			const defaultData = [{
				done: false,
				content: '할 일 목록1'
			}]
			const todosData = JSON.parse(localStorage.getItem('todos')) || defaultData;
			const todos = ref(todosData);  //변경될 값

			function addTodo () {
				if (newTodo.value) {
					todos.value.push({
						done: false,
						content: newTodo.value
					});
					newTodo.value = '';
				}
				saveData();
			}

            function doneTodo (todo) {
				todo.done = !todo.done
				saveData();
			}

			function removeTodo (index) {
				todos.value.splice(index, 1);
				saveData();
			}

			function saveData () {
				const storageData = JSON.stringify(todos.value);
				localStorage.setItem('todos', storageData);
			}

			onBeforeMount(() => {
                alert(`간단한 todo리스트입니다.`);
            });

			return {
				todos,
				newTodo,
				addTodo,
				doneTodo,
				removeTodo,
				saveData
			}
		}
	}
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  margin-top: 60px; 
}
.done {text-decoration: line-through;}
</style>
