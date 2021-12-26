<script>

  let vote = "";

  let options = [
    {
      value: '长城',
      description: '长城 -- ',
      votes: 20
    },
    {
      value: '故宫',
      description: '故宫 -- ',
      votes: 10
    },
    {
      value: '颐和园',
      description: '颐和园 -- ',
      votes: 5
    }
  ];

  $: total = options.reduce((sum, current) => {
    return sum + current.votes;
  }, 0);

  const voteHandler = (index) => {
    options[index].votes += 1;
    options = options.sort((a, b) => b.votes - a.votes);
	}
</script>

<svelte:head>
  <title>Vote</title>
</svelte:head>

<div class="wrapper">
  <div class="content is-medium">
    <h1>春游活动</h1>
    <div class="tags">
      <span class="tag">One</span>
      <span class="tag">Two</span>
      <span class="tag">Three</span>
      <span class="tag">Four</span>
      <span class="tag">Five</span>
      <span class="tag">Six</span>
      <span class="tag">Seven</span>
      <span class="tag">Eight</span>
      <span class="tag">Nine</span>
      <span class="tag">Ten</span>
    </div>
    <p>四月的下午不要错过。</p>
  </div>
  <div class="field">
    <div class="control">
      <div class="columns is-flex-direction-column is-mobile">
        {#each options as { value, description, votes}, i (value)}
          <div class="column" style="padding-bottom: 2rem;">
            <div class="columns">
              <div class="column progress_bar_wrapper" style="flex-basis: calc((100% - 120px)*{votes/total});">
                <div class="progress_bar" style=""></div>
              </div>
              <div class="column bar_summary_wrapper">
                <div class="bar_summary">
                  <span class="votes">{votes}票</span><span>({Math.round(votes/total*100)}%)</span>
                </div>
              </div>
            </div>
            <label class="radio">
              <input type="radio" bind:group={vote} value={value} on:click={() => {voteHandler(i)}}/>
              <!-- <input type="radio" bind:group={vote} value={option.id} on:change={() => {voteHandler(option.id)}}/> -->
              {description}
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
  .wrapper {
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

    .bar_summary_wrapper {
      padding: 0;
    }

  }


</style>
