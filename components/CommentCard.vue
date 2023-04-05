<template>
    <div class="card text-left shadow-lg px-7 py-4 rounded-lg border-2 border-grey my-5">
        <h2 class="font-bold mb-2 ">{{comment.username}}</h2>
          
        <p>{{comment.comment}}</p>
        
    </div>
    
</template>

<script setup>
const {comment} = defineProps(['comment'])
</script>

<style scoped>
</style>