<template>
    
    <div class="grid grid-cols-1 gap-5 w-2/3 mx-auto mt-10">
        <div v-for="comment in allData">
            <CommentCard :comment="comment"/> 
        </div>  
        
        <button class="rounded-full mx-auto bg-green-400 font-bold text-white w-1/4 px-4 py-2" @click="loadMore">load more</button>  
    </div>
</template>

<script>

    export default {
        data(){
            return{
                comments:[],
                tempComments:[],
                limit: 10,
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
            }
        },
        methods:{
            async loadComments(){
                const response = await fetch("http://localhost:8000/api/v1/comments");
                const jsonData = await response.json();
                this.comments = jsonData

            },
            loadMore() {
                this.limit += 10
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