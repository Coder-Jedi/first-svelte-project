<script>
  import { data } from "../stores";

  let data_value;
  let items;
  export let listType;

  data.subscribe((value) => {
    data_value = value;
    items = data_value.filter((value) => value.entryType === listType);
  });

  const handleDeleteItem = (id) => {
    data.update((oldData) => {
      return oldData.filter((value) => value.id != id);
    });
  };
</script>

<div class="lists-container">
  {#each items as item}
    <div class={`container ${listType === "income" ? "income" : "expense"}`}>
      <div class="amount"><span>{item.amount}</span></div>
      <div class="description">
        <span>{item.description}</span>
      </div>
      <div class="delete">
        <button on:click={() => handleDeleteItem(item.id)}>delete</button>
      </div>
    </div>
  {/each}
</div>

<style>
  .lists-container {
    display: flex;
    flex-direction: column;
    min-height: 300px;
    width: 470px;
    background-color: white;
    padding: 5px;
  }
  .container {
    display: flex;
    width: 450px;
    min-height: 50px;
    margin: 5px;
  }
  .amount {
    width: 120px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: black;
    color: white;
    font-size: 20px;
  }
  .description {
    width: 100%;
    display: flex;
    align-items: center;
    padding: 0 10px;
    color: white;
  }
  .delete {
    width: 90px;
    display: flex;
    align-items: center;
    margin-right: 5px;
  }
  .delete button {
    color: white;
    background-color: black;
    width: 100%;
    margin: 0;
  }
  .expense {
    background-color: crimson;
  }
  .income {
    background-color: forestgreen;
  }
</style>
