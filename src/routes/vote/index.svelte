<script>

  import Vote from './Vote.svelte';

  let datasource = [
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

  let customClass = "my_vote";
</script>

<svelte:head>
  <title>Vote</title>
</svelte:head>

<div class="wrapper">
  <div class="box">
    <div class="content is-medium">
      <h1>春游活动</h1>
      <div class="tags">
        <span class="tag is-primary">投票中...</span>
        <span class="tag is-link">截止时间XXX</span>
        <span class="tag is-info">可带一名家属</span>
        <span class="tag is-success">Four</span>
        <span class="tag is-warning">Five</span>
        <span class="tag is-danger">Six</span>
        <span class="tag">Seven</span>
        <span class="tag">Eight</span>
        <span class="tag">Nine</span>
        <span class="tag">Ten</span>
      </div>
      <p>一年一度的春游，四月的下午不要错过。</p>
    </div>
  </div>

  <h1 class="title is-2">Default Component</h1>
  <Vote {datasource} />

  <h1 class="title is-2">Component with Slots</h1>
  <Vote class="my_vote" {datasource}>
    <div slot="progress" let:stat class="columns is-align-items-center" >
      <div class="column is-narrow">
        <span class="tag is-dark" style="width: 80px;">
          {Math.round(stat.votes/stat.total*10000)/100}%
        </span>
      </div>
      <div class="column">
        <progress class="progress is-small" value={stat.votes/stat.total*100} max="100">{Math.round(stat.votes/stat.total*10000)/100}%</progress>
      </div>
    </div>
    <div slot="description" let:desc class="box" style="display:inline-block;width:calc(100% - 50px);margin-left:10px;" >
      {desc}
    </div>
  </Vote>

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
  }

	:global(.my_vote [type=radio]) {
		width: 30px;
    height: 30px;
    vertical-align: middle;
	}
</style>
