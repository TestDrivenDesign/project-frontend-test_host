<template>
	<div class="job-list">
		<p>Ordered by: {{ order }}</p>
		<ul>
			<li v-for="job in orderedJobs" :key="job.id">
				<h2>{{ job.title }} in {{ job.location }}</h2>
				<p>£{{ job.salary }}</p>
			</li>
		</ul>
	</div>
</template>

<script lang="ts">
import { computed, defineComponent, type PropType } from 'vue';
import type Job from '@/types/Job';
import type OrderTerm from '@/types/OrderTerm';

export default defineComponent({
	props: {
		jobs: {
			required: true,
			type: Array as PropType<Job[]>,
		},
		order: {
			required: true,
			type: String as PropType<OrderTerm>,
		},
	},
	setup(props) {
		const orderedJobs = computed(() => {
			return [...props.jobs].sort((a: Job, b: Job) => {
				return a[props.order] > b[props.order] ? 1 : -1;
			});
		});

		return { orderedJobs };
	},
});
</script>

<style scoped></style>
