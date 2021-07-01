<template>
    <div class="pure-g" style="justify-content:center;text-align: center;">
        <div class="pure-u">
            <h1 >{{title}}</h1>
            <h5 >{{description}}</h5>
        </div>
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