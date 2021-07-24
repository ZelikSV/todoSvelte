<script>
  export let title;
  export let likeCount;
  export let complete;
  export let id;
  export let changeTodo;

  let isLiked = false;

  const handleLikeTodoItem = () => {
    isLiked = !isLiked;
    changeTodo({ title, likeCount, complete, id });
  };

  const handleTodoDone = evt => {
    complete = evt.target.checked;
    changeTodo({ title, likeCount, complete: evt.target.checked, id });
  };
</script>

<style lang="scss">
  .todoItem__wrapper {
    width: 450px;
    background: rgb(41, 114, 128);
    list-style-type: none;
    padding: 10px 20px;
    margin-bottom: 10px;
    border-radius: 5px;
    position: relative;
    p {
      color: #ddd;
      font-size: 20px;
      line-height: 40px;
      margin: 0;
    }
    div {
      display: flex;
      .icon-like {
        color: red;
        display: inline-block;
        margin-right: 5px;
        cursor: pointer;
        user-select: none;
      }
      span {
        color: #ddd;
      }
    }
    .checkedKey {
      position: absolute;
      top: 50%;
      right: 0;
      transform: translate(-50%, -50%);
      cursor: pointer;
      user-select: none;
    }
  }
</style>

<li class="todoItem__wrapper">
  <p>{title}</p>
  <div>
    {#if isLiked}
      <span class="icon-like" on:click={handleLikeTodoItem}>&#x2764;</span>
    {:else}
      <span class="icon-like" on:click={handleLikeTodoItem}>&#x2661;</span>
    {/if}
    <span>{isLiked ? ++likeCount : --likeCount}</span>
    <input
      type="checkbox"
      class="checkedKey"
      checked={complete}
      on:change={handleTodoDone} />
  </div>
</li>
