<template>
    <div>
        <h2>{{ person.name }}</h2>
        <h3>{{ person.codingProwess }}</h3>
        <h3>{{ person.price }}</h3>
        <button @click="increment">Add</button>
    </div>
</template>

<script>
    import { ref } from "vue";
    const props = defineProps({
    Person: Object,
    });
    const clicked = ref(0);
    function increment() {
    clicked.value++;
}
</script>

<style lang="scss" scoped>

</style>