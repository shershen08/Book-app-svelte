<script>
    import {createEventDispatcher} from 'svelte'
    import Button from './button.svelte'
    export let details;
    const dispatch =  createEventDispatcher()
    function purchaseBook(){
        dispatch('buy', details.title)
    }
     function removeBook(){
        dispatch('remove', details.title)
    }

</script>

<style lang="scss">
$aqua: aqua;
    div{
        margin: 1rem;
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26)
    }

    h1{
        font-size: 1.25rem;
        margin: 0.25rem 0;
    }

    h2{
        font-size: 1rem;
        margin: 0.25rem 0;
        color:$aqua;
    }

    p{
        margin: 0.25rem 0;
    }

  
</style>


<div>
    <h1> {details.title} </h1>
    <h2> {details.pages}</h2>
    <h2> {details.price}</h2>
    <p> {details.description}</p>
    <Button on:click={purchaseBook}>Buy</Button>
    <Button on:click={removeBook}>remove</Button>

</div>