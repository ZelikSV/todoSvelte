<script>
  import TodoItem from "../TodoItem/TodoItem.svelte";
  export let listTodos;

  let list = [...listTodos];

  const editListItems = editedItem => {
    const indItem = list.findIndex(elem => elem.id === editedItem.id);
    const newList = [...list];

    newList.splice(indItem, 1, editedItem);
    list = [...newList];
  };
</script>

<style>

</style>

<ul>
  {#each list as { title, id, likeCount, complete } (id)}
    <TodoItem {title} {likeCount} {complete} {id} changeTodo={editListItems} />
  {/each}
</ul>
