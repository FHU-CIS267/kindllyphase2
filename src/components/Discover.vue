<template>
    <div class="browse-kindllys">
        <h2>Browse Kindllys</h2>
        
        <div class="kindlly-groups">

            <div class="kindlly-group" v-for="section in discoverKindllys" :key="section.sectionName">
                <h3>{{section.sectionName}}</h3>
                <div class="kindlly-list">
                    <Kindlly 
                        v-for="kindlly in section.kindllys"
                        :key="kindlly.id"
                        :Kindlly="kindlly"
                        v-on:add-kindlly="addKindlly($event, section.kindllys)"
                    />
                </div>
            </div>

        </div>

    </div>
</template>

<script>
import Kindlly from '@/components/Kindlly.vue';
import {EventBus} from '../main.js';

export default {
    name: 'Discover',
    components: {
        Kindlly
  },
  data () {
      return {
          "discoverKindllys": [
            {
                "sectionName": "Trending",
                "kindllys": [
                    {
                        "id": 1,
                        "description": "Buy your CS professor a coffee!",
                        "points": 25,
                        "cost": 1,
                        "creator": {
                            "username": "CoTo",
                            "firstName": "Cody",
                            "lastName": "Todd",
                            "avatar": "cody.jpg"
                        },
                        "isLiked": false
                    },
                    {
                        "id": 2,
                        "description": "Send a text to your dad asking him about his day.",
                        "points": 15,
                        "cost": 0,
                        "creator": {
                            "username": "DaYa",
                            "firstName": "Dallas",
                            "lastName": "Yarnell",
                            "avatar": "dallas.jpg"
                        },
                        "isLiked": true
                    },
                    {
                        "id": 3,
                        "description": "Bring your roomate an iced tea with an encouraging note on the cup!",
                        "points": 15,
                        "cost": 1,
                        "creator": {
                            "username": "CoTo",
                            "firstName": "Cody",
                            "lastName": "Todd",
                            "avatar": "cody.jpg"
                        },
                        "isLiked": false
                    },
                    {
                        "id": 4,
                        "description": "Send a text to your mom thanking her.",
                        "points": 10,
                        "cost": 0,
                        "creator": {
                            "username": "DaYa",
                            "firstName": "Dallas",
                            "lastName": "Yarnell",
                            "avatar": "dallas.jpg"
                        },
                        "isLiked": true
                    }
                ]
            },
            {
                "sectionName": "For Young People ",
                "kindllys": [
                    {
                        "id": 5,
                        "description": "Buy your CS professor a coffee!",
                        "points": 25,
                        "cost": 1,
                        "creator": {
                            "username": "CoTo",
                            "firstName": "Cody",
                            "lastName": "Todd",
                            "avatar": "cody.jpg"
                        },
                        "isLiked": false
                    },
                    {
                        "id": 6,
                        "description": "Send a text to your dad asking him about his day.",
                        "points": 15,
                        "cost": 0,
                        "creator": {
                            "username": "TheRealDaYarnell",
                            "firstName": "Dallas",
                            "lastName": "Yarnell",
                            "avatar": "dallas.jpg"
                        },
                        "isLiked": true
                    },
                    {
                        "id": 7,
                        "description": "Bring your roomate an iced tea with an encouraging note on the cup!",
                        "points": 15,
                        "cost": 1,
                        "creator": {
                            "username": "DaYa",
                            "firstName": "Cody",
                            "lastName": "Todd",
                            "avatar": "cody.jpg"
                        },
                        "isLiked": false
                    },
                    {
                        "id": 8,
                        "description": "Send a text to your mom thanking her.",
                        "points": 10,
                        "cost": 0,
                        "creator": {
                            "username": "TheRealDaYarnell",
                            "firstName": "Dallas",
                            "lastName": "Yarnell",
                            "avatar": "dallas.jpg"
                        },
                        "isLiked": true
                    }
                ]
            },
            {
                "sectionName": "On the Cheap ",
                "kindllys": [
                    {
                        "id": 5,
                        "description": "Buy your CS professor a coffee!",
                        "points": 25,
                        "cost": 1,
                        "creator": {
                            "username": "CoTo",
                            "firstName": "Cody",
                            "lastName": "Todd",
                            "avatar": "cody.jpg"
                        },
                        "isLiked": false
                    },
                    {
                        "id": 6,
                        "description": "Send a text to your dad asking him about his day.",
                        "points": 15,
                        "cost": 0,
                        "creator": {
                            "username": "DaYa",
                            "firstName": "Dallas",
                            "lastName": "Yarnell",
                            "avatar": "dallas.jpg"
                        },
                        "isLiked": true
                    },
                    {
                        "id": 7,
                        "description": "Bring your roomate an iced tea with an encouraging note on the cup!",
                        "points": 15,
                        "cost": 1,
                        "creator": {
                            "username": "CoTo",
                            "firstName": "Cody",
                            "lastName": "Todd",
                            "avatar": "cody.jpg"
                        },
                        "isLiked": false
                    },
                    {
                        "id": 8,
                        "description": "Send a text to your mom thanking her.",
                        "points": 10,
                        "cost": 0,
                        "creator": {
                            "username": "DaYa",
                            "firstName": "Dallas",
                            "lastName": "Yarnell",
                            "avatar": "dallas.jpg"
                        },
                        "isLiked": true
                    }
                ]
            }
        ]
      }
  },
  created (){
        EventBus.$on('KINDLLY_ADDED', (kindlly) => {
            // kindllys.splice(kindllys.indexOf(kindlly), 1);
            this.discoverKindllys.forEach(section => {
                section.kindllys.forEach(kindllyObject => {
                    if (kindlly.id == kindllyObject.id) {
                        section.kindllys.splice(section.kindllys.indexOf(kindlly), 1);
                    }
                });
            });
        })
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.browse-kindllys {
	width: 66.666666%;
}

.browse-kindllys h3 {
	margin: 2rem 0 0 0rem;
	font-family: Roboto;
	font-weight: 400;
	font: size 1.8rem;
	text-transform: capitalize;
}

.kindlly-list {
	display: flex;
	justify-content: flex-start;
	flex-wrap: wrap;
	margin-left: -1rem;
	/* overflow: auto; */
}

</style>
