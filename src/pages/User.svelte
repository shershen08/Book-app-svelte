<script>
let name = 'mike';

const timeout = 1000;
const waitFunction = (() => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve(timeout)
        }, timeout)
    })
})()
</script>


{#await waitFunction}
	<!-- promise is pending -->
	<p>waiting for the waitFunction to resolve...</p>
{:then value}
	<!-- promise was fulfilled -->
	<p>The value is {timeout}</p>
{:catch error}
	<!-- promise was rejected -->
	<p>Something went wrong: {error.message}</p>
{/await}

<h2>User {name} page </h2>