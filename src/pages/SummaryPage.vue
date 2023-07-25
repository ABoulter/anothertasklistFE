<template>
    <main class="px-4 py-5 my-5 text-center" style="min-height: 50vh;">
        <h1 class="display-5 fw-bold mt-4" v-if="showToggleMessage">You're working hard!</h1>
        <h1 class="display-5 fw-bold mt-4" v-else>Find something cool to do!</h1>
        <div class="col-lg-6 mx-auto">
            <p class="lead mb-4" v-if="showToggleMessage">You've completed <strong>{{ completedTasksNumber }}</strong> tasks
                so far</p>
        </div>
    </main>
</template>

<script setup>
import { computed } from "vue";
import { storeToRefs } from "pinia"
import { useTaskStore } from "../stores/task"

const store = useTaskStore()
const { completedTasks, uncompletedTasks } = storeToRefs(store)

const completedTasksNumber = completedTasks.value.length


const showToggleMessage = computed(() => completedTasks.value.length > 0)

</script>