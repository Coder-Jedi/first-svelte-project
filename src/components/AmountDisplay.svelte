<script>
  export let amount = 1000;
</script>

<div class={`container ${amount >= 0 ? "positive" : "negative"}`}>
  <h2>{amount}</h2>
</div>

<style>
  .container {
    background-color: cornflowerblue;
    width: 300px;
    height: 100px;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .positive {
    background-color: forestgreen;
  }
  .negative {
    background-color: crimson;
  }
</style>
