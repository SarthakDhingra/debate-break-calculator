<template>
    <div class="has-text-centered">
        <h1 class="title is-1" style="color:white">{{title}}</h1>
        <h5 class="subtitle is-5" style="color:white">{{description}}</h5>
    </div>
</template>

<script>

export default {
    name: "Header",
    data() {
        return {
            title: "Debate Breaker",
            description: "Determine the points needed to advance to outrounds at debating tournaments"
        }
    }
}
</script>

<style>

h1 {
    color:white
}
</style>