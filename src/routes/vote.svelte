<script>
  let vote = "故宫";

  let options = [
    "长城", "故宫", "颐和园"
  ];
</script>

<svelte:head>
  <title>Vote</title>
</svelte:head>

<div class="content">
  <h1>春游活动</h1>

  <div class="field">
    <div class="control">
      <div class="columns is-flex-direction-column is-mobile">
        {#each options as option}
          <div class="column is-full">
            <div class="columns bar">
              <div class="column is-narrow">
                <div class="active_bar" style="width: 200px;">

                </div>
              </div>
              <div class="column is-narrow">
                <div class="bar_summary">

                </div>
              </div>
              <div class="column is-narrow">
                <div class="inactive_bar">

                </div>
              </div>
            </div>
            <label class="radio">
              <input type="radio" bind:group={vote} value={option} />
              {option}
            </label>
          </div>
        {/each}
      </div>
    </div>
  </div>

  <div class="field is-grouped is-grouped-centered">
    <div class="control">
      <button class="button is-primary">Submit</button>
    </div>
    <!-- <div class="control">
      <button class="button is-link is-light">Cancel</button>
    </div> -->
  </div>

</div>

<style>
  .content {
    width: 100%;
    max-width: var(--column-width);
    margin: var(--column-margin-top) auto 0 auto;
  }
  
  .radio {
    width: 100%;
  }
</style>
