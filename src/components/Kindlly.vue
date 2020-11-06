<template>
    <div class="kindlly">
        <div class="header">
            <div class="info">
                <h4>{{Kindlly.description}}</h4>
                <div>
                    <p class="cost" v-if="Kindlly.cost == 0"><span></span><span class="faded">FREE</span></p>
                    <p class="cost" v-if="Kindlly.cost == 1"><span>$</span><span class="faded">$$</span></p>
                    <p class="cost" v-if="Kindlly.cost == 2"><span>$$</span><span class="faded">$</span></p>
                    <p class="cost" v-if="Kindlly.cost == 3"><span>$$$</span></p>
                </div>
            </div>

            <p class="points">
                <span class="value">+{{Kindlly.points}}</span><br />
                <span class="label">KP</span>
            </p>
        </div>
        <div class="creator-info">
            <img v-bind:src="AvatarPath" alt="" class="creator-img"/>
            <div class="creator-row">
                <p>Creator</p>
                <p class="creator-name">{{Kindlly.creator.username}}</p>
            </div>
        </div>
        <section class="buttons">
            <a href="" class="more-button button">···</a>
            <a @click.prevent="Kindlly.isLiked = false" v-if="Kindlly.isLiked" class="like-button button"><i class="el el-heart"></i></a> 
            <a @click.prevent="Kindlly.isLiked = true" v-else class="like-button button"><i class="el el-heart-empty"></i></a>
            <a @click="addKindlly" class="add-button button"><i class="el el-plus-sign"></i> </a>
        </section>
    </div>
</template>

<script>
import {EventBus} from '../main.js'

export default {
	name: 'Kindlly',
	props: {
		Kindlly: Object
	},
    data: function() {
        return {
        }
	},
	methods: {
		addKindlly: function() {
			EventBus.$emit('KINDLLY_ADDED', this.Kindlly);
		}
	},
	computed: {
		AvatarPath: function() {
			return require('../assets/img/' + this.Kindlly.creator.avatar);
		}
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.kindlly {
	border-radius: 1rem;
	background: rgba(247, 127, 0, 0.1);
	margin: 1rem 1rem 3rem 1rem;
	display: flex;
	flex-direction: column;
    text-align: left;
	background: linear-gradient(145deg, #dad4ba, #fffddd);
	box-shadow: 30px 30px 60px #dad4ba, -30px -30px 60px #ffffe4;
	transition: all 0.5s ease-in-out;
}

.kindlly:hover {
	box-shadow: inset 30px 30px 60px #dad4ba, -30px -30px 60px #ffffe4;
}

.kindlly .header {
	position: relative;
}

.kindlly .header h4 {
	font-size: 1.25rem;
}

.kindlly .header .info {
	margin: 1rem 1rem;
}
.kindlly .header .info > div {
	margin-top: 0.5rem;
}

.browse-kindllys .kindlly {
	max-width: 40%;
}

.kindlly .header .points {
	background: #d62828;
	color: white;
	padding-top: 0.7rem;
	font-size: 1.1rem;
	font-weight: 800;
	line-height: 0.66666666rem;
	height: 2.5rem;
	width: 2.5rem;
	border-radius: 50%;
	text-align: center;
	position: absolute;
	top: -1rem;
	right: -1rem;
}
.kindlly .header .points .label {
	font-weight: 200;
	font-size: 0.66rem;
}

.kindlly .header .faded {
	opacity: 0.3;
}

.kindlly .creator-info {
	display: flex;
	margin-top: auto;
}

.kindlly .creator-info p:first-child {
	font-variant-caps: all-petite-caps;
	font-size: 0.8em;
	opacity: 0.5;
}

.kindlly .creator-info img {
	max-height: 50px;
	padding: 0rem 0.5rem 0rem 1rem;
	border-radius: 50%;
}

.kindlly .buttons {
	background: #fcbf49;
	display: flex;
	justify-content: flex-end;
	margin: 0.5rem 0 0 0;
	padding: 0.25rem 1rem;
	border-radius: 0 0 1rem 1rem;
}

.kindlly .button {
	font-size: 1.8rem;
	padding: 5px;
	text-decoration: none;
	color: #eee;
	border-radius: 2rem;
}

.button:hover {
	cursor: pointer;
}

.kindlly .more-button {
	margin-right: auto;
	font-size: 1.8rem;
	line-height: 1.8rem;
	text-decoration: none;
	color: #eee;
	height: 2rem;
	width: 2rem;
	border-radius: 50%;
	display: block;
	margin: auto auto auto 0;
}

.kindlly .more-button:hover {
	/* opacity: 0.5; */
	background: #f2eccf44;
}
</style>