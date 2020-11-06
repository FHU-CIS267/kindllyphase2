<template>
    <div class="kindlly">
        <h2>{{kindlly.description}}</h2>

        <p>{{kindlly.creator.username}}</p>
        <button v-if="!kindlly.isLiked" @click="a">
        <button v-if="kindlly.isLiked" @click="a">

        <button @click="addKindlly">
    </div>
</template>

<script>
import {eventBus} from "../main.js"
export default {
    name: "Kindlly",
    components: {},
    props: {
        kindlly: Object
    },
    data() {
        return{
            // sections: this.sections
        };
    },
    methods: {
        toggleLike: function() {
            console.log(this.kindlly.id + " was liked!");
            this.kindlly.isLiked = !this.kindlly.isLiked;
        },
        addKindlly() {
            eventBus.$emit("KINDLLY_ADDED", this.kindlly);
        }
    }
}
</script>

<style scoped>
.kindlly {
    border: 1px solid cadetblue;
    border-radius: 2rem;
    margin: 1rem;
}
</style>