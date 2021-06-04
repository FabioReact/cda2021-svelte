<script>
	let username = ''
	let password = ''
	function submitHandler(event) {
		event.preventDefault()
		console.log({
			username: username,
			password: password,
		})
	}
</script>

<form on:submit={submitHandler}>
	<label for="username">Username:</label>
	<input bind:value={username} type="text" id="username" name="username">
	<label for="password">Password:</label>
	<input bind:value={password} type="password" id="password" name="password">
	<button type="submit">Login</button>
</form>

<style>
	button {
		display: block;
		margin: 0 auto;
	}
</style>