<script>
    let tasks = [
        {
            id: 1,
            title: "Task 1",
            completed: false
        },
        {
            id: 2,
            title: "Task 2",
            completed: false
        },
        {
            id: 3,
            title: "Task 3",
            completed: false
        }
    ];

    function toggleTask(index) {
        tasks[index].completed = !tasks[index].completed;
        // Trigger reactivity
        tasks = [...tasks];
    }
</script>

<div class="flex flex-col justify-center items-center min-h-screen">
    <div class="border rounded-md border-orange-400 p-10">
        <h2 class="text-orange-300 text-2xl font-bold">Todos</h2>

        <div>
            {#each tasks as task, index}
            <div>
                <input type="checkbox" id="task-{task.id}" checked={task.completed} on:change={() => toggleTask(index)} />
                <label for="task-{task.id}" class="ml-2">{task.title}</label>
            </div>
            {/each}
        </div>

        <div>
            <h3>Completed Tasks</h3>
            {#each tasks as task, index}
                {#if task.completed}
                    <div>
                        <input type="checkbox" id="completed-task-{task.id}" checked={task.completed} on:change={() => toggleTask(index)} />
                        <label for="completed-task-{task.id}" class="ml-2">{task.title}</label>
                    </div>
                {/if}
            {/each}
        </div>
    </div>
</div>
