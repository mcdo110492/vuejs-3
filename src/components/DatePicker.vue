<template>
    <h1>One Date Selection</h1>
    <VueDatePicker v-model="date"></VueDatePicker>
    <h1>Minimum Date Selection</h1>
    <VueDatePicker v-model="minDate" :min-date="new Date()"></VueDatePicker>
    <h1>Maximum Date Selection</h1>
    <VueDatePicker v-model="maxDate" :max-date="maxDateLimit"></VueDatePicker>
    <h1>Date Range Selection</h1>
    <VueDatePicker v-model="rangeDate" range />
</template>

<script setup lang="ts">
import { computed, ref, onMounted } from "vue"
import VueDatePicker from "@vuepic/vue-datepicker"
import "@vuepic/vue-datepicker/dist/main.css"
import { addMonths, getMonth, getYear } from 'date-fns'

const date = ref()
const minDate = ref()
const maxDate = ref()
const rangeDate = ref()

const maxDateLimit = computed(() => addMonths(new Date(getYear(new Date()), getMonth(new Date())), 2))

onMounted(() => {
    const startDate = new Date()
    const endDate = new Date(new Date().setDate(startDate.getDate() + 7))
    rangeDate.value = [startDate, endDate]
})

</script>