<script>

  let vote = "故宫";
  let total = 100;
  const options = [
    {
      id: 0,
      description: '长城',
      votes: 20
    },
    {
      id: 1,
      description: '故宫',
      votes: 10
    },
    {
      id: 2,
      description: '颐和园',
      votes: 5
    }
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
            <div class="columns">
              <div class="column progress_bar_wrapper" style="flex-basis: {option.votes/total*100}%;">
                <div class="progress_bar" style=""></div>
              </div>
              <div class="column">
                <div class="bar_summary" style="">
                  <span class="votes">{option.votes}票</span><span>({option.votes/total*100}%)</span>
                </div>
              </div>
            </div>
            <label class="radio">
              <input type="radio" bind:group={vote} value={option.id} />
              {option.description}
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

<style type="text/scss">
  .content {
    width: 100%;
    max-width: var(--column-width);
    margin: var(--column-margin-top) auto 0 auto;

    .radio {
      width: 100%;
    }

    .progress_bar_wrapper {
      display: flex;
      flex-direction: column;
      flex-grow: 0;
      align-self: center;
    
      .progress_bar {
        border-top: 1px solid black;
      }
    }

  }


</style>
