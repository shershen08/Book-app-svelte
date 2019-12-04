<script>
	import Button from './../components/button.svelte'
	import Purchase from './../components/purchase.svelte'
	import BooksList from './../components/booksList.svelte'
	
	import { books } from '../store/store.js';

	let title = '';
	let pages = 0;
	let price = 0;
	let description = '';

	let purchases = [];
	let valid = false;
	let descriptionLength = 0;

	function setTitle(event){
		title = event.target.value;
	}

	function handleKeydown(){
		if(event.target.value && event.target.value.length > 10){
			valid = true;
		} else {
			valid = false
		}
		descriptionLength = event.target.value.length
	}

	function addBook(){
		const newBook = {
			title,
			pages,
			description,
			price
		};
		books.update(books => books.concat(newBook));
		
		title = pages = description = ''
		price = pages = 0
		valid = false
	}

	function purchaseBook(event){
		const selectedTitle= event.detail.title;
		purchases = purchases.concat({
			...$books.find(book => book.title === selectedTitle)
		});
	}


	function removeBook(event){
		const selectedTitle= event.detail.title;
		books.update(books => books.filter(book => book.title !== selectedTitle));
	}

</script>

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
		<input type="number" id="price" value={price} bind:value={price} min="1" max="1000"/> $
	</div>

	<div>
		<label for="description">Description</label>
		<textarea rows="3" id="description" on:keydown={handleKeydown} bind:value ={description}/>
		<small>Symbols: {descriptionLength}</small>
	</div>

	<!-- valid:{valid} -->
	<Button on:click={addBook} isDisabled={!valid}>ADD Book</Button>

</section>

<!-- {@debug books} -->
<BooksList on:buy={purchaseBook} on:remove={removeBook}/>

<hr>

<Purchase books ={purchases} /> 

