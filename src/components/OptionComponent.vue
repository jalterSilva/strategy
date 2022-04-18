<template>
    <select class="form-select" v-model="selectedStatusFilter">
       <option :value="0">All</option>
       <option v-for="option in options" :key="option.value" :value="option.value">
            {{ option.text }}
       </option>
    </select>
</template>

<script>

export default{
    name: "OptionComponent",
    props:{
        options: Array,      
        selectedStatusFilter: Number
    }
}
</script>