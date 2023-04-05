<template>
    <div>
        <p>Product details for {{ id }}</p>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Eligendi, libero commodi? Eum dolorem voluptates quis vero. Ullam libero facilis consectetur, quia voluptates itaque atque doloremque similique error facere fugit quo.</p>   
    </div>
</template>

<script setup>
    const { id } = useRoute().params
</script>

<style scoped>
h2 {
    margin-bottom: 20px;
    font-size: 16px;
}

p {
    margin: 20px 0;
}
</style>