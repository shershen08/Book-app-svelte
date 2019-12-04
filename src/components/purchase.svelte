<script>
    export let books;
    $: summ = books.reduce((a,b) => a + b.price, 0);
</script>


<style>
    ul{
        list-style: none;
        margin: 1rem;
        padding:0;
    }

    li{
        font-size:1.5rem;
        margin: 1rem;
    }

</style>

{#if books.length !== 0}
    <h2> Cart </h2>
    <ul>
        {#each books as book}
            <li> <strong>{book.title}</strong> / {book.price} $</li>
        {/each}
    </ul>

    <h2> Total </h2>
    <p>{books.length} books for {summ}$</p>
{/if}