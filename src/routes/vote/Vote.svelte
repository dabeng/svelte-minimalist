<script>

  let vote = "";

  export let datasource;

  $: total = datasource.reduce((sum, current) => {
    return sum + current.votes;
  }, 0);

  const voteHandler = (index) => {
    datasource[index].votes += 1;
    datasource = datasource.sort((a, b) => b.votes - a.votes);
	}
</script>

<div class={`control${$$props.class ? ' ' + $$props.class : ''}`}>
  <!-- <div class={`control${' ' + clazz || ''}`}></div> -->
  <div class="columns is-flex-direction-column is-mobile">
    {#each datasource as { value, description, votes}, i (value)}
      <div class="column" style="padding-bottom: 2rem;">
        <slot name="progress" stat={{votes, total}}>
        <div class="columns">
          <div class="column progress_bar_wrapper" style="flex-basis: calc((100% - 120px)*{votes/total});">
            <div class="progress_bar" style=""></div>
          </div>
          <div class="column bar_summary_wrapper">
            <span class="votes">{votes}票</span><span>({Math.round(votes/total*100)}%)</span>
          </div>
        </div>
      </slot>
        <label class="radio">
          <input type="radio" bind:group={vote} value={value} on:click={() => {voteHandler(i)}}/>
          <!-- <input type="radio" bind:group={vote} value={option.id} on:change={() => {voteHandler(option.id)}}/> -->
          
          <slot name="description" desc={description}>
            {description}
          </slot>
        </label>
      </div>
    {/each}
  </div>
</div>

<style type="text/scss">

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

</style>
