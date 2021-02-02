<script lang="ts">
  import { onMount } from "svelte";
  import _ from "lodash";
  import * as d3 from "d3";

  let state: string = "loading";
  let data: Object = { cases: "...", todayCases: "..." };

  onMount(async () => {
    let result = await fetch(
      "https://api.coronavirus.data.gov.uk/v1/data?" +
        "filters=areaType=utla;areaCode=E06000052&" +
        'structure={"date":"date","newCases":"newCasesByPublishDate", "totalCases":"cumCasesBySpecimenDate", "deaths": "cumDeaths28DaysByPublishDate"}'
    ).then((result) => result.json());

    console.log(result);
    console.table(result.data);
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
