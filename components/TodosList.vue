<template>
	<ul class="mx-19">
		<li v-for="task in tasks" :key="tasks.indexOf(task)" @click="check(task)">
		</li>
	</ul>
</template>

<style lang="css">
	.checkbox {
		background-color: rgb(192 38 211)

	}
</style>

<script lang="ts">
import { defineComponent } from 'vue';

interface TasksInterface {
	msg: String,
	checked: boolean
}

export default defineComponent({
	data() {
		return {
			tasks: [
				{
					msg: " ",
					checked: false
				}
			]
		}
	},
	methods: {
		check(task: TasksInterface) {
			if (task.checked !== true) {
				task.checked = true;
				return
			}
			task.checked = false
		}
	},
	async fetch() {
		this.tasks = await fetch('http://localhost:8000/tasks')
			.then(res => res.json())
	},
	mounted() {
		axios
      .get('http://localhost:8000/tasks')
      .then(task => (this.task = ))
	}
})
</script>
