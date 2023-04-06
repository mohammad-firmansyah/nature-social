<template>
        <header class="shadow-md bg-white">
                <nav class="container text-center mx-auto p-4 md:flex md:justify-between ">
                    <ul>
                        <li class="text-lg font-bold text-green-400 mb-2 md:mt-2">Nature Social</li>
                    </ul>  
                    <ul>
                        <li :class="searchClass" >
                            <input type="text" @click="turnOn" @input="turnOn" @keyup="turnOff" @keyup.enter="search" name="search" class="p-2 text-sm focus:outline-none " placeholder="search here">   
                            <font-awesome-icon icon="fa-solid fa-search"/>
                        </li>
                    </ul>  
                
                </nav>
        </header>

            <div class="container mx-auto w-100">
                <div class="block gap-5 w-2/3 mx-auto my-10 text-center">
                    <div v-for="comment in allData">
                        <CommentCard :comment="comment"/> 
                    </div>  
                
                    <button class="rounded-full mx-auto bg-green-400 font-bold text-white md:w-1/4 px-4 py-2" @click="loadMore">load more</button>  
                </div>
            </div>

            <footer class="p-2 text-center mt-10 font-bold text-gray">
                &copy 2023 firman
            </footer> 
    
</template>

<script>

    export default {
        data(){
            return{
                comments:[],
                tempComments:[],
                limit: 10,
                 active: false
            }
        },
        created(){
            this.loadComments()
        },
        computed:{
            allData(){
                this.comments.forEach((e,i) => {
                    if (i < (this.limit-1) ) {
                        let temp = {"username":e.username,"comment":e.comment}
                        this.tempComments.push(temp)
                    }
                })

                return this.tempComments
            },
            searchClass() {
            if (this.active) {
                return "w-50 text-lg font-bold text-green-400 bg-gray border border-2 text-left pl-1 md:pl-2 md:pr-5  rounded-lg border-green-400"
            } else {
                return "w-50 text-lg font-bold text-green-400 bg-gray border border-2 text-left pl-1 md:pl-2 md:pr-5  rounded-lg"

            }
        }
        },
        methods:{
            async loadComments(){
                const response = await fetch("http://localhost:8000/api/v1/comments")
                const jsonData = await response.json()
                this.comments = jsonData

            },
            loadMore() {
                this.tempComments = []
                this.limit += 10
            },
            turnOff(e) {
            if (e.target.value == "") {

                this.active = false
            }
            },
            turnOn(e) {
                this.active = true
            },
            async search(e) {
                let key = e.target.value

                const response = await fetch("http://localhost:8000/api/v1/search/"+key);
                const jsonData = await response.json();
                this.comments = jsonData
                this.tempComments = []
                this.limit = 10

            }
        }
    }
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