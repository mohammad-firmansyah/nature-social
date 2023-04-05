<template>
    <div>
        <header class="shadow-md bg-white">
            <nav class="container text-center mx-auto p-4 md:flex md:justify-between ">
                <ul>
                    <li class="text-lg font-bold text-green-400 mb-2 md:mt-2">Nature Social</li>
                </ul>  
                <ul>
                    <li :class="searchClass" >
                        <input type="text" @click="turnOn" @input="turnOn" @keyup="turnOff" name="search" class="p-2 text-sm focus:outline-none " placeholder="search here">   
                        <font-awesome-icon icon="fa-solid fa-search"/>
                    </li>
                </ul>  
                
            </nav>
        </header>

        
         <!-- output -->

         <div class="container mx-auto w-100">
            <slot />
         </div>

         <footer class="p-2 text-center mt-10 font-bold text-gray">
            &copy 2023 firman
         </footer> 
    </div>
</template>

<script>

export default {
    data () {
        return {
            active: false
        }
    },
    computed:{
        searchClass(){
            if (this.active) {
                return "w-50 text-lg font-bold text-green-400 bg-gray border border-2 text-left pl-1 md:pl-2 md:pr-5  rounded-lg border-green-400"
            } else {
                return "w-50 text-lg font-bold text-green-400 bg-gray border border-2 text-left pl-1 md:pl-2 md:pr-5  rounded-lg"

            }
        }
    },
    methods:{
        turnOff(e){
            if (e.target.value == "") {
                
                this.active = false
            }
        },
        turnOn(e){
            this.active = true
        },
       
    }
}
</script>

<style scoped>

.router-link-exact-active{
     color:red;
}

</style>