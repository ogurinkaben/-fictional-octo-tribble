 <template>
 	<form @submit="addUser">
 		<input type="text" v-model="username" name="username" placeholder="Add User">
 		<input type="submit" value="Add">
 	</form>
 </template>

 <script >
 	export default {
 		name: "AddUser",
 		data:function () {
 			return {
 				userTitle:''
 			}
 		},
 		methods: {
 			addUser(e) {
 				e.preventDefault();
 				if (this.username === "") {
 					alert("error");
 				} else {
 					 				const newUser = {
 					username:this.username,
 					marked:false			
 				}
 				this.$emit("add-user", newUser);
 				this.username="";
 				}			
 			}
 			
 		}
 	}

 </script>

 <style scoped>
 	form {
 	display:flex;
 }
 form input[type="text"] {
 	flex: 10;
 	padding: 5px;
 }
  form input[type="submit"] {
  	flex: 2;  } 
 </style>
