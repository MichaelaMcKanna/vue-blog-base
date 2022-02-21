<template>
	<div class="home">
		<h1>Home</h1>
		<div v-if="error">{{ error }}</div>
		<div v-if="posts.length"><PostList :posts="posts" /></div>
		<div v-else>Loading...</div>
	</div>
</template>

<script>
import PostList from '../components/PostList';
import getPosts from '../composables/getPosts.js';
export default {
	name: 'Home',
	components: { PostList },
	setup() {
		const { load, error, posts } = getPosts();

		load();

		return { posts, error };
	},
	// setup() {
	// 	const writerOne = ref({ name: 'micha', age: 28 });
	// 	const writerTwo = reactive({ name: 'chance', age: 32 });

	// 	const updateWriterOne = () => {
	// 		writerOne.value.name = 'Old';
	// 		writerOne.value.age = 40;
	// 	};
	// 	const updateWriterTwo = () => {
	// 		writerTwo.name = 'Young';
	// 		writerTwo.age = 20;
	// 	};
	// 	return {
	// 		writerOne,
	// 		writerTwo,
	// 		updateWriterOne,
	// 		updateWriterTwo,
	// 	};
	// },
	// created() {
	// 	console.log('created');
	// },
	// mounted() {
	// 	console.log('mounted');
	// },
};
</script>
