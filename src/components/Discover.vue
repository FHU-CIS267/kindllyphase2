<template>
    <div class = "discover">
        <h1> Discover </h1>
        <div
        class ="kindlly-section"
        v-for ="section in sections"
        :key ="section.name"
        >

        <h2> {{section.name}} </h2>

        <Kindlly
        v-for ="kindlly in section.kindlly"
        :key ="kindlly.id"
        :kindlly ="kindlly"
        @kindlly-added="onKindllyAdded"
        />
        </div>
    </div>
</template>

<script>
import Kindlly from "@/components/Kindlly.vue"

export default {
    name: "Discover",
    components: {Kindlly},
    props: {
        //sections: Array
    },
    data() {
        return{
            sections: [

            ],
        };
    },
    computed: {
        age() {
            return 0;
        }
    },
    methods: {
        onKindllyAdded: function(kindlly) {
            console.log(kindlly);
        }
    }
};
</script>

<style scoped>
.discover{
    width: 100%;
}
</style>