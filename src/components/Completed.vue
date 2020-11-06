<template>
    <div class="kindlly">
        <div class="header">
            <div class="info">
                <h4>{{Completed.description}}</h4>
                <div>
                    <p class="cost" v-if="Completed.cost == 0"><span></span><span class="faded">FREE</span></p>
                    <p class="cost" v-if="Completed.cost == 1"><span>$</span><span class="faded">$$</span></p>
                    <p class="cost" v-if="Completed.cost == 2"><span>$$</span><span class="faded">$</span></p>
                    <p class="cost" v-if="Completed.cost == 3"><span>$$$</span></p>
                    <p class="date">{{age}}</p>
                </div>
            </div>
            <p class="points">
                <span class="value">+{{Completed.points}}</span><br />
                <span class="label">KP</span>
            </p>
        </div>
        <section class="buttons">
			<a @click="$emit('uncomplete-kindlly', Completed)" class="complete-button button"> Completed</a>
        </section>
    </div>
</template>

<script>
import ago from 's-ago'

export default {
	name: 'Completed',
	props: {
		Completed: Object
	},
    data: function() {
		return {
		dateAdded: new Date()
		}
	},
	computed: {
		age() {
		return ago(this.dateAdded);
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
	font-size: 1.5rem;
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

.header .info > div {
	display: flex;
	align-content: center;
	justify-content: space-between;
}

.kindlly .buttons {
	background: #f77f00;
	display: flex;
	justify-content: flex-end;
	margin: 0.5rem 0 0 0;
	padding: 0.25rem 1rem;
	border-radius: 0 0 1rem 1rem;
}

.kindlly .button {
	padding: 5px;
	text-decoration: none;
	color: #eee;
	border-radius: 2rem;
}

.button:hover {
	cursor: pointer;
}

.complete-button {
	width: 100%;
	text-align: left;
	font-size: 1rem;
	text-transform: uppercase;
	font-weight: 800;
	margin: 1rem 0rem 1rem 0rem;
}

.delete-button {
	width: 20%;
	text-align: right;
	font-size: 0.8rem;
	line-height: 1rem;
	text-transform: uppercase;
	margin: 1.5rem 0 1.2rem 0rem;
	opacity: 0;
}

.kindlly:hover .delete-button {
	opacity: 0.9;
}

.kindlly.completed h4 {
	text-decoration: line-through;
}

.kindlly.completed .points {
	display: none;
}

</style>
