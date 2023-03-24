<script lang="ts">
import { defineComponent, reactive, toRefs, ref } from 'vue';
import JobList from './components/JobList.vue';
import type Job from './types/Job';
import type OrderTerm from './types/OrderTerm';

export default defineComponent({
	name: 'App',
	components: { JobList },
	setup() {
		const jobs = ref<Job[]>([
			{
				title: 'engineer',
				location: 'Leeds',
				salary: 30000,
				id: '1',
			},
			{
				title: 'gardener',
				location: 'Hull',
				salary: 20000,
				id: '2',
			},
			{
				title: 'dancer',
				location: 'Coventry',
				salary: 25000,
				id: '3',
			},
			{
				title: 'operator',
				location: 'Rugby',
				salary: 15000,
				id: '4',
			},
		]);

		const order = ref<OrderTerm>('title');

		function handleClick(term: OrderTerm) {
			order.value = term;
		}

		return { jobs, handleClick, order };

		// const name = ref('Larry');
		// const age = ref<number | string>(25);

		// return { name, age };

		// const state = reactive({
		// 	name: 'John',
		// 	age: 25 as number | string,
		// });

		// state.name = 'M'

		// return { ...toRefs(state) };
	},
	// data() {
	// 	return {
	// 		name: 'Anna',
	// 		age: 25 as number | string,
	// 	};
	// },
	// methods: {
	// 	changeName(name: string) {
	// 		this.name = name;
	// 	},

	// 	changeAge(age: number | string) {
	// 		this.age = age;
	// 	},
	// },
});
</script>

<template>
	<div class="app">
		<button @click="handleClick('title')">order by title</button>
		<button @click="handleClick('salary')">order by salary</button>
		<button @click="handleClick('location')">order by location</button>
		<JobList :jobs="jobs" :order="order" />
		<!-- <p>{{ name }} - {{ age }}</p>
		<button @click="changeName('Jenny')">Change name</button>
		<button @click="changeAge(35)">Change age</button> -->
	</div>
</template>

<style scoped></style>
