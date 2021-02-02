<script lang="ts">
  import { onMount } from "svelte";

  let state: string = "loading";
  let data: Object = { cases: "...", todayCases: "..." };

  onMount(async () => {
    let result = await fetch(
      "https://api.coronavirus.data.gov.uk/v1/data?" +
        "filters=areaType=nation;areaName=england&" +
        'structure={"date":"date","newCases":"newCasesByPublishDate"}'
    ).then((result) => result.json());

    console.log(result);
  });
</script>

<main>
  <h1>Template</h1>
</main>

<style lang="scss">
  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

  @media (min-width: 480px) {
    h1 {
      max-width: none;
    }
  }
</style>
