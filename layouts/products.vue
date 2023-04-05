<template>
    <div>
        <header class="shadow-sm bg-white">
            <nav class="container mx-auto p-4 flex justify-between">
                <ul class="flex gap-4">
                    <li>
                        <NuxtLink to="/products">Merch</NuxtLink>
                    </li>
                </ul>
            </nav>
        </header>
        

            <!-- output -->

            <div clas="container mx-auto">
                <slot />
            </div>

         <footer class="shadow-sm bg-white">
                <nav class="container mx-auto p-4 flex justify-between">
                    <ul class="flex gap-4">
                        <li>
                            <NuxtLink to="/" class="font-bold">Home</NuxtLink>
                        </li>
                        <li>

                            <NuxtLink to="/dashboard">About</NuxtLink>
                        </li>  
                        <li>

                            <NuxtLink to="/products">Products</NuxtLink>
                        </li>  
                    </ul>
                </nav>
            </footer>

    </div>
</template>

<script setup>

</script>

<style scoped>
.router-link-exact-active {
    color: red;
}
</style>