<script>
    let newName = "";
    let newSum;
    let todoList = [];
    function add() {
        if (newName !== "") {
            todoList = [
                ...todoList,
                {
                    name: newName,
                    sum: newSum,
                    completed: false,
                },
            ];
            console.log({ todoList });
            newName = "";
            newSum = "";
    }
    }
    function remove(index) {
        todoList.splice(index, 1);
        todoList = todoList;
    }
</script>

<main>
    <h1>Учёт расходов</h1>
    <form on:submit|preventDefault={add}>
        <label for="">название:</label>
        <input bind:value={newName} />
        <label for="">сумма:</label>
        <input bind:value={newSum} />
        <button class="add-todo" on:click={add}><span>Добавить</span></button>
    </form>
    <table class="todos">
        <tr class="headtable">
            <td class="name">название</td>
            <td class="sum">сумма </td>
            <td class="do">действие</td>
        </tr>
        {#each todoList as item, index}
            <tr class="todo" class:completed={item.completed}>
                <td class="todo__text">{item.name} </td>
                <td class="todo__text">{item.sum} </td>
                <td class="todo__buttons">
                    <button class="delete" on:click={() => remove(index)}>
                        удалить
                    </button>
                </td>
            </tr>
        {/each}
    </table>
</main>

<style>
    form {
        width: 100%;
        max-width: 100px;
        display: flex;
        margin-bottom: 1rem;
        flex-direction: column;
    }
    .add-todo {
        background-color: rgb(49, 221, 49);
        border-radius: 20px;
        margin-top: 20px;
    }
    input {
        border-radius: 10px;
        border-color: gray;
    }
    table {
        padding: 0px;
    }
    td {
        margin: 0px;
        width: 300px;
        border: solid 1px;
    }
    .headtable {
        background-color: rgba(180, 178, 178, 0.74);
    }
    .delete {
        background-color: rgb(49, 221, 49);
        border-radius: 20px;
    }

    /* main {
        display: flex;
        flex-direction: column;
        min-height: 100%;
        padding: 5vmin;
        box-sizing: border-box;
    }
    form {
        width: 100%;
        max-width: 500px;
        display: flex;
        align-items: center;
        margin-bottom: 1rem;
    }
    input {
        flex-grow: 1;
        width: 0;
        border-radius: 10px;
        border-color: rgb(148, 148, 148);
        font-size: 1.2rem;
        margin: 0;
    }
    .todos {
        width: 100%;
        max-width: 500px;
    }
    .todo {
        display: flex;
        padding: 20px;
        border-radius: 20px;
        box-shadow: 0 0 15px rgb(0 0 0 / 20%);
        background-color: hsla(0, 0%, 100%, 0.2);
        margin-top: 1rem;
        font-size: 1.2rem;
        justify-content: space-between;
        align-items: center;
    }
    .todo__buttons {
        display: flex;
        align-items: center;
        margin-left: 1rem;
    }
    .todo button {
        width: 32px;
        height: 32px;
        padding: 4px;
        margin: 0;
        flex-shrink: 0;
    }
    h1 {
        text-align: left;
        font-size: 1.5rem;
        margin: 2em 0;
    }
    button {
        background-color: transparent;
        border: none;
    }
    button.delete,
    button.delete:hover {
        color: brown;
        transition: color 100ms ease-out;
    }
    .todo.completed {
        color: slategray;
    }
    .todo.completed .todo__text {
        text-decoration: linethrough;
    }
    .todo.completed button {
        color: silver;
    } */
</style>
