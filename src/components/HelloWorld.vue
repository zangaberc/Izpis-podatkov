<template>
	<div class="services">
		<div class="blabla">
			<br/>
			<h1>Izpis podatkov iz api-ja v oblačke</h1>
       		<p>
				Prikaz izpisa podatkov (Naslov, Opis in Id) iz api-ja
				(https://jsonplaceholder.typicode.com/posts).
			</p>
			<div class="postavitev-podatkov">
				<div class="post" v-for="post in posts" :key="post.id">
					<div class="naslov">
						<p style="float: left">
						{{post.id}}
						</p>
						<h4>	
							Naslov: {{post.title}}
						</h4>
					</div>
					<div class="opis">
						<p>
							Opis: {{post.body}}
						</p>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>
<script>
import {Loading } from 'element-ui';
import axios from 'axios'
	export default{
		name:'services',
		data (){
			return{
				posts: []
			}
		},
		components: {
		[Loading.name]: Loading
		},
		mounted() {
			var self = this;
			axios.get('https://jsonplaceholder.typicode.com/posts').then( function(res) {
				self.posts = res.data;
			})
			.catch(function(error){
				console.log('error: ', error);
			})
		}
	}
</script>
<style>
p {
	font-size: 20px;
}
</style>

<style scoped>
	.postavitev-podatkov {
		width: 1000px;
		margin: 0 auto;
	}
	.post {
		background-color: white;
		margin-bottom: 20px;
		padding: 10px 20px;
	}
	.naslov {
		background-color:#4da6ff;
		padding: 10px 20px;
		-webkit-border-top-left-radius: 20px;
		-webkit-border-top-right-radius: 20px;
		-moz-border-radius-topleft: 20px;
		-moz-border-radius-topright: 20px;
		border-top-left-radius: 20px;
		border-top-right-radius: 20px;
	}
	.opis {
		background-color: #cce6ff;
		padding: 10px 20px;
		-webkit-border-bottom-right-radius: 20px;
		-webkit-border-bottom-left-radius: 20px;
		-moz-border-radius-bottomright: 20px;
		-moz-border-radius-bottomleft: 20px;
		border-bottom-right-radius: 20px;
		border-bottom-left-radius: 20px;
	}
	h3 {
		text-align: left;
	}
	p {
		text-align: left;
	}
</style>