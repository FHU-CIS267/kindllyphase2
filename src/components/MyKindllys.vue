<template>
    <div class="my-kindllys">
        <h1>My Kindllys<h1/>
        <MyKindlly
        v-for="kindlly in myKindllys"
        :key ="kindlly.id"
        :myKindlly ="kindlly"
        />
    </div>
</template>

<script>
import MyKindlly from "@/components/MyKindlly.vue"
import {eventBus} from "../main.js"

export default {
    name: "MyKindllys",
    components: {MyKindlly},
    props: {
        //myKindllys: Array
    },
    data(){
        return{
            myKindllys: [
                {
                    id: 10,
                    description: "Buy your girlfriend some flowers",
                    creator: {username: "CoTo"},
                    isLiked: true
                },
                {
                    id: 20,
                    description: "Give your professor a hug",
                    creator: {username: "DarYar"},
                    isLiked: false
                }
            ]
        };
    },
    methods: {

    },
    created() {
        eventBus.$on("KINDLLY_ADDED", kindlly => {
            this.myKindllys.push(kindlly);
        });
    }
};
</script>

<style scoped>
.my-kindllys {
    width: 100%;
}
</style>