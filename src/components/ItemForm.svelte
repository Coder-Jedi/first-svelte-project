<script>
  import { createEventDispatcher } from "svelte";

  let entryType = "";
  let amount = 0;
  let description = "";

  const dispatch = new createEventDispatcher();

  const handleSave = () => {
    const formData = {
      entryType,
      amount,
      description,
      id: Math.random(),
    };
    dispatch("saveForm", formData);
  };
  const handleCancel = () => {
    dispatch("cancel");
  };
</script>

<form>
  <table>
    <tr>
      <label for="entryType">Entry type:&nbsp; &nbsp; &nbsp;</label>
      <select id="entryType" bind:value={entryType}>
        <option value="income">Income</option>
        <option value="expense">Expense</option>
      </select>
    </tr>
    <tr>
      <label for="amount">Amount:&nbsp; &nbsp; &nbsp;</label>
      <input type="number" bind:value={amount} />
    </tr>
    <tr>
      <label for="description">Description:&nbsp; &nbsp; &nbsp;</label>
      <input type="text" bind:value={description} />
    </tr>
    <tr
      ><button type="submit" on:click|preventDefault={handleSave}>Save</button>
      &nbsp; &nbsp; &nbsp; &nbsp;
      <button type="reset" on:click|preventDefault={handleCancel}>Cancel</button
      >
    </tr>
  </table>
</form>

<style>
  label {
    color: white;
    display: inline;
    font-size: 18px;
  }
  table {
    line-height: 35px;
  }
  button {
    margin-top: 15px;
  }
</style>
