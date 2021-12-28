<script>

  let vote = "";

  let options = [
    {
      value: '长城',
      description: '长城 -- 八达岭长城 + 闯关游戏',
      votes: 20
    },
    {
      value: '故宫',
      description: '故宫 -- 角楼咖啡☕️ + 桌游',
      votes: 10
    },
    {
      value: '颐和园',
      description: '颐和园 -- 万寿山佛香阁 + 龙船 + 听鹂馆宫廷菜',
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
