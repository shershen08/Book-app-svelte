<script>
	import Book from './book.svelte'
	import Button from './button.svelte'
	import Purchase from './purchase.svelte'
	let title = '';
	let pages = 0;
	let price = 0;
	let description = '';

	let books =[];
	let purchases = [];

	function setTitle(event){
		title = event.target.value;
	}

	function addBook(){
		const newBook = {
			title,
			pages,
			description,
			price
		};
		books = books.concat(newBook)
		
		title = pages = description = ''
	}

	function purchaseBook(event){
		const selectedTitle= event.detail;
		purchases = purchases.concat({
			...books.find(book => book.title === selectedTitle)
		});
	}


	function removeBook(event){
		const selectedTitle= event.detail;
		books = books.filter(book => book.title !== selectedTitle);
	}

</script>

<style>
	h1 {
		color: purple;
		
	}

	section{
		margin: auto;
		width :30rem;
		
	}

	label,input,textarea{width: 100%}
</style>

<section>
	<div> 
		<label for="title">Title</label>
		<input type="text" id="title" value={title} on:input={setTitle}/>
	</div>

	<div>
		<label for="pages"> pages</label>
		<input type="number" id="price" value={pages} bind:value={pages}/>
	</div>

		<div>
		<label for="price"> price</label>
		<input type="number" id="price" value={price} bind:value={price}/>
	</div>

	<div>
		<label for="description">Description</label>
		<textarea rows="3" id="description" bind:value ={description}/>
	</div>

	<Button on:click={addBook}>ADD Book</Button>

</section>

<section>
{#if books.length === 0}
	<p>
	   Add a new book 
	</p>
	{:else}
	{#each books as book}
		<Book details={book} 
		on:buy={purchaseBook}
		on:remove={removeBook}
		/>
	{/each}
{/if}

</section>

<hr>

<section>
	<Purchase books ={purchases}  /> 
</section>

