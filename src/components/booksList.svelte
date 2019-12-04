<script>
import Book from './book.svelte'
import { books } from '../store/store.js';
import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();
    
   function purchaseBook(e) {
		dispatch('buy', {
            title: e.detail
        });
    }
    function removeBook(e) {
		dispatch('remove', {
            title: e.detail
        });
	}
</script>

<section>
<!-- {$books.length} -->
{#if $books.length === 0}
	<p>
	   Add a new book 
	</p>
	{:else}
	{#each $books as book}
		<Book details={book} 
		on:buy={purchaseBook}
		on:remove={removeBook}
		/>
	{/each}
{/if}

</section>