<template>
    <div class="my-kindllys">
        <div class="fixed-container">
            <h2>My Kindllys</h2>
            <MyKindlly
                v-for="kindlly in myKindllys"
                :key="kindlly.id"
                :myKindlly="kindlly"
                v-on:remove-kindlly="removeKindlly($event)"
                v-on:complete-kindlly="updateMyKindllys($event)"
            />

            <h3>Completed</h3>
            <Completed class="completed"
                v-for="kindlly in completedKindllys"
                :key="kindlly.id"
                :Completed="kindlly"
                v-on:uncomplete-kindlly="updateMyKindllys($event)"
            />

        </div>
    </div>
</template>

<script>
import MyKindlly from '@/components/MyKindlly.vue';
import Completed from '@/components/Completed.vue';
import {EventBus} from '../main.js';

export default {
    name: 'MyKindllys',
    components: {
        MyKindlly,
        Completed
    },
    data () {
        return {
            "myKindllys": [
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
                    "isLiked": true,
                    "dateAdded": "2020-10-20T01:29:55.422Z",
                    "isCompleted": false
                },
                {
                    "id": 8,
                    "description": "Send a note to your sibling expressing appreciation.",
                    "points": 15,
                    "cost": 0,
                    "creator": {
                        "username": "DaYa",
                        "firstName": "Dallas",
                        "lastName": "Yarnell",
                        "avatar": "dallas.jpg"
                    },
                    "isLiked": true,
                    "dateAdded": "2020-10-20T01:29:55.422Z",
                    "isCompleted": false
                }
            ],
            "completedKindllys": [
                {
                    "id": 11,
                    "description": "Send a text to your mom thanking her.",
                    "points": 10,
                    "cost": 0,
                    "creator": {
                        "username": "DaYa",
                        "firstName": "Dallas",
                        "lastName": "Yarnell",
                        "avatar": "dallas.jpg"
                    },
                    "isLiked": true,
                    "dateAdded": "2020-10-20T01:29:55.422Z",
                    "isCompleted": true
                }
            ]
        }
    },
    methods: {
		removeKindlly: function(myKindlly) {
			this.myKindllys.splice(this.myKindllys.indexOf(myKindlly), 1);
        },
        updateMyKindllys: function(kindlly) {
            if (kindlly.isCompleted == null) {
                kindlly.isCompleted = false;
                this.myKindllys.push(kindlly);
            }
            else if (kindlly.isCompleted == false){
                kindlly.isCompleted = true;
                this.myKindllys.splice(this.myKindllys.indexOf(kindlly), 1);
                this.completedKindllys.push(kindlly);
            }
            else if (kindlly.isCompleted == true) {
                kindlly.isCompleted = false;
                this.completedKindllys.splice(this.completedKindllys.indexOf(kindlly), 1);
                this.myKindllys.push(kindlly);
            }
        }
    },
    created (){
        EventBus.$on('KINDLLY_ADDED', (kindlly) => {
            this.updateMyKindllys(kindlly);
        })
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.my-kindllys {
	width: 33.33333%;
}

.my-kindllys .fixed-container {
	position: sticky;
	top: 6rem;
}

.my-kindllys h2,
.my-kindllys h3 {
	margin: 0 0 0 1rem;
}

.my-kindllys h3 {
	margin-top: 2rem;
	font-family: Roboto, sans-serif;
	font-weight: 400;
	font: size 1.8rem;
	text-transform: capitalize;
}

.my-kindllys .kindlly .header h4 {
	font-size: 1.5rem;
}

.my-kindllys .header .info > div {
	display: flex;
	align-content: center;
	justify-content: space-between;
}

.my-kindllys .buttons {
	background: #f77f00;
}

.my-kindllys .complete-button {
	width: 100%;
	text-align: left;
	font-size: 1rem;
	text-transform: uppercase;
	font-weight: 800;
	margin: 1rem 0rem 1rem 0rem;
}

.my-kindllys .delete-button {
	width: 20%;
	text-align: right;
	font-size: 0.8rem;
	line-height: 1rem;
	text-transform: uppercase;
	margin: 1.5rem 0 1.2rem 0rem;
	opacity: 0;
}

.my-kindllys .kindlly:hover .delete-button {
	opacity: 0.9;
}

.my-kindllys .kindlly.completed h4 {
	text-decoration: line-through;
}

.my-kindllys .kindlly.completed .points {
	display: none;
}

</style>