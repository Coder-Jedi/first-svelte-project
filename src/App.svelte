<script>
  import Layout from "./components/Layout.svelte";
  import AmountDisplay from "./components/AmountDisplay.svelte";
  import { data } from "./stores";

  data.set([
    {
      entryType: "income",
      amount: 1000,
      description: "small pay first",
      id: Math.random(),
    },
    {
      entryType: "income",
      amount: 1000,
      description: "small pay second",
      id: Math.random(),
    },
    {
      entryType: "expense",
      amount: 100,
      description: "samosa chat at Redi",
      id: Math.random(),
    },
    {
      entryType: "expense",
      amount: 250,
      description: "haircut at Salon",
      id: Math.random(),
    },
  ]);
</script>

<main>
  <Layout />
</main>

<style>
</style>
