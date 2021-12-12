<template>
    <select @change="onChange" class="form-select mt-10 block w-full border p-3 rounded" v-model='selected'>
        <option value="0">Select Country</option>
        <option v-for="country in countries" :value="country.ID" :key="country.ID"> {{country.Country}}</option>
    </select>
</template>

<script>
export default {
    name: 'SelectCountry',
    props: ['countries'],
    data() {
        return {
            selected: 0
        }
    },
    methods: {
        onChange() {
            let country = this.countries.find((country) => country.ID === this.selected)
            this.$emit('updateCountry', country)
        }
    }
}
</script>