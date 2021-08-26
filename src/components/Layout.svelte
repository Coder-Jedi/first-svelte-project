<script>
  import ItemForm from "./ItemForm.svelte";
  import Modal from "./Modal.svelte";
  import { data } from "../stores";
  import ItemsList from "./ItemsList.svelte";
  import AmountDisplay from "./AmountDisplay.svelte";

  let title = "expense calculator";
  let showModal = false;
  let data_value;
  let total_amount = 0;

  data.subscribe((value) => {
    data_value = value;
    total_amount = 0;
    data_value.forEach((value) => {
      if (value.entryType === "income") total_amount += value.amount;
      else total_amount -= value.amount;
    });
    console.log("total_amount: ", total_amount);
  });

  const toggleModal = () => {
    showModal = !showModal;
  };
  const handleAddItem = () => {
    toggleModal();
  };
  const handleSaveForm = (e) => {
    data.update((oldData) => [...oldData, e.detail]);
    toggleModal();
  };
</script>

<Modal {showModal} on:click={toggleModal}>
  <ItemForm on:saveForm={(e) => handleSaveForm(e)} on:cancel={toggleModal} />
</Modal>
<div class="outer-container">
  <div class="title-container">
    <h1>{title}</h1>
  </div>
  <div class="amount-container">
    <AmountDisplay amount={total_amount} />
  </div>
  <div class="edit-options-container">
    <button on:click={handleAddItem}>Add New Item</button>
  </div>
  <div class="lists-outer-container">
    <div class="income-list">
      <ItemsList listType="income" />
    </div>
    <div class="expense-list">
      <ItemsList listType="expense" />
    </div>
  </div>
</div>

<style>
  .outer-container {
    display: flex;
    flex-direction: column;
    width: 100%;
    align-items: center;
  }
  .title-container {
    height: 100px;
    color: crimson;
    background-color: black;

    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    text-transform: uppercase;
  }

  .amount-container {
    height: 200px;

    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .edit-options-container {
    height: 120px;

    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .edit-options-container button {
    width: 190px;
    height: 56px;
    font-size: 20px;
    color: #29f;
    background-color: black;
  }
  .lists-outer-container {
    width: 100%;

    display: grid;
    grid-template-columns: auto auto;
  }
  .income-list {
    display: flex;
    justify-content: center;
  }
  .expense-list {
    display: flex;
    justify-content: center;
  }
</style>
