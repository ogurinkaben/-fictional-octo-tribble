<template>
	<div class="user">
		<p>
		<span>{{user.username}} </span> 
	</p>
	<button v-on:click="$emit('delete-user',user.id )" class="del">x</button>
	</div>
</template>

<script>
	export default {
		name: "User",
		props: ["user"],
		
	}
</script>

<style scoped>
.user {
	background: #f1f1f1;
	padding: 10px 12px;
	display: flex;
	min-height: 40px;
	align-items: center;
	justify-content: space-between;
	margin:1rem auto;
	box-shadow: 0 10px 30px rgba(0,0,0,0.23);
	max-width:50%; 
}
	.is-complete {
		text-decoration: line-through;
	}

	.del {
		background: #f00;
		height: 40px;
		width: 40px;
		border-radius: 50%;
		font-size: 20px;
		color: #fff;
		border:none;
		cursor: pointer;
	}

</style>
