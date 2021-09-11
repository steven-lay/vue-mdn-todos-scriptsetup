<script setup>
import { ref } from "vue";

const emit = defineEmits(["add-todo"]);

let label = ref("");

function onSubmit() {
	if (label.value !== "") {
		emit("add-todo", label.value);
		label.value = "";
	}
}
</script>

<template>
	<form @submit.prevent="onSubmit">
		<h2 class="label-wrapper">
			<label for="new-todo-input"> What needs to be done? </label>
		</h2>
		<input
			id="new-todo-input"
			v-model="label"
			class="input__lg"
			type="text"
			name="new-todo"
			autocomplete="off"
		/>
		<button
			type="submit"
			:disabled="!label.length"
			class="btn btn__primary btn__lg"
		>
			Add
		</button>
	</form>
</template>