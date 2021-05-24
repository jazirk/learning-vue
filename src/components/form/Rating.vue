<template>
    <ul>
        <li><button :class="{active: selected === 'one'}" @click="select('one')" type="button">One</button></li>
        <li><button :class="{active: selected === 'two'}" @click="select('two')" type="button">Two</button></li>
    </ul>
</template>

<script>
export default {
    props: ['ratingValue'],
    emits: ['update:ratingValue'],
    data() {
        return {
            selected: this.ratingValue
        }
    },
    methods: {
        select(value) {
            this.selected = value;
            this.$emit('update:ratingValue', value);

        }
    }
}
</script>

<style scoped>
    .active {
        background-color:red;
    }
</style>