<template>
	<div class="mb-4" v-if="resume.educationStore.educationsForm.length > 0">
		<h2 class="text-slate-600 text-xl font-semibold flex items-center gap-1 mb-2">
			<AcademicCapIcon class="w-7 h-7" />
			Educations
		</h2>
		<div
			v-for="(item, index) in resume.educationStore.educationsForm"
			:key="index"
			class="rounded bg-slate-200 p-2 text-justify relative group hover:bg-slate-300 mb-1"
		>
			<div class="hidden gap-2 absolute top-2 right-2 bg-slate-500 p-1 rounded group-hover:flex">
				<PencilSquareIcon class="w-5 h-5 cursor-pointer fill-slate-100" @click="resume.educationStore.editEducation(item)" />
				<XCircleIcon class="w-5 h-5 cursor-pointer fill-slate-100" @click="resume.educationStore.deleteEducationData(item)" />
			</div>
			<div class="flex justify-between mb-2">
				<h3 class="text-xl font-semibold">{{ item.name }}</h3>
				<p class="text-gray-500">{{ isShowDate(item) }}</p>
			</div>
			<div class="text-gray-500">
				{{ item.degree }}
			</div>
		</div>
	</div>
</template>

<script setup>
import { useResumeStore } from '../stores/resume'
import { MONTH_ARRAY } from '../constans'
import { PencilSquareIcon, XCircleIcon } from '@heroicons/vue/24/solid'
import { AcademicCapIcon } from '@heroicons/vue/24/outline'

const resume = useResumeStore()

function isShowDate(item) {
	return `${MONTH_ARRAY[item.startDate.month]} ${item.startDate.year} - ${MONTH_ARRAY[item.endDate.month]} ${item.endDate.year}`
}

</script>
