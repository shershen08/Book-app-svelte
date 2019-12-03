 <script>
      import Grid from "svelte-grid";
      import gridHelp from "svelte-grid/build/helper/index.mjs";

      const id = () => "_" + Math.random().toString(36).substr(2, 9);

      let items = [
        gridHelp.item({ x: 0, y: 0, w: 2, h: 2, id: id() }),
        gridHelp.item({ x: 2, y: 0, w: 2, h: 2, id: id() })
      ];
    </script>

    <Grid items={items} cols={3} bind:items={items} let:item={item}>
      <div>{item.id}</div>
    </Grid>

     <style>
      :global(.svlt-grid-shadow) { /* Back shadow */
        background: pink;
      }
      :global(.svlt-grid-container) {
        background: #eee;
      }
      :global(.svlt-grid-resizer::after) { /* Resizer color */
        border-color: white !important;
      }
      :global(.svlt-grid-item) {
        border: 2px solid;
      }
    </style>