<style>
  button{
        font : larger;
        padding: 0.15rem 0.5rem;
        background-color: #1b1a1a;
        border: 1px solid  aliceblue ;
        cursor: pointer;
        color: white;
    }
button:disabled {
    background-color: #ccc;
}

</style>

<script>
   export let isDisabled = false;
</script>

<button on:click disabled={isDisabled}>
    <slot/>
</button>