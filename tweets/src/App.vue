<template>
	<div id="app">
		<img src="./assets/logo.png">
		<HelloWorld/>
		<div class="columns">
			<div class="column">
        <button class="is-primary button" @click="reverse">Reverse</button>
        <transition-group name="tweets" tag="div">
				<tweet-component v-for="tweet in tweets" :tweet="tweet" :key="tweet.id"></tweet-component>
        </transition-group>
			</div>
		</div>
	</div>
</template>

<script>
  import Vue from "vue";
  import "../node_modules/bulma/css/bulma.css"
  import "../node_modules/@fortawesome/fontawesome-free/css/all.css"
	import HelloWorld from "./components/HelloWorld";
	const tweets = [
		{
			id: 1,
			name: "James",
			handle: "@jokerjames",
			img: "/static/matthew.png",
			tweet: "If you don't succeed, dust yourself off and try again.",
			likes: 10
		},
		{
			id: 2,
			name: "Fatima",
			handle: "@fantasticfatima",
			img: "/static/molly.png",
			tweet: "Better late than never but never late is better.",
			likes: 12
		},
		{
			id: 3,
			name: "Xin",
			handle: "@xeroxin",
			img: "/static/elyse.png",
			tweet: "Beauty in the struggle, ugliness in the success.",
			likes: 18
    },
    	{
			id: 4,
			name: "James12",
      handle: "@jokerjames",
      img: "/static/molly.png",
			tweet: "If you don't succeed, dust yourself off and try again.",
			likes: 14
		},
		{
			id: 5,
			name: "Fatima21",
      handle: "@fantasticfatima",
      img: "/static/elyse.png",
			tweet: "Better late than never but never late is better.",
			likes: 15
		},
		{
			id: 6,
			name: "Xin33",
			handle: "@xeroxin",
			img: "/static/matthew.png",
			tweet: "Beauty in the struggle, ugliness in the success.",
			likes: 16
		}
	];
	Vue.component("tweet-component", {
		template: `<div class="tweet">
      <div class="box">
        <article class="media">
          <div class="media-left">
            <figure class="image is-64x64">
              <img :src="tweet.img" alt="Image">
            </figure>
          </div>
          <div class="media-content">
            <div class="content">
              <p>
                <strong>{{tweet.name}}</strong> <small>{{tweet.handle}}</small>
                <br>
                {{tweet.tweet}}
              </p>
            </div>
              <div class="level-left">
                <a class="level-item">
                  <span class="icon is-small"><i class="far fa-heart"></i></span>
                  <span class="likes">{{tweet.likes}}</span>
                </a>
              </div>
          </div>
        </article>
        <div class="control has-icons-left has-icons-right">
        <input class="input is-small" v-bind:placeholder="'Hi !'+tweet.name" />
        <span class="icon is-small is-left">
          <i class="fas fa-envelope"></i>
        </span>
      </div>
    </div>
      </div>
      
    </div>`,
		props: {
			tweet: Object
		}
	});
	export default {
		name: "App",
		components: {
			HelloWorld
		},
		data: () => {
			return {
				tweets: tweets
			};
    },
    methods: {
      reverse:()=>{
        this.tweets = tweets.reverse();
      }
    },
	};
</script>

<style>
#app {
	font-family: "Avenir", Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
  margin-left:200px;
  margin-right:200px;
}
.tweets-move{
  transition:transform 1s;
}
</style>
