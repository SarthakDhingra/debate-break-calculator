<template>
    <div class="pure-g" style="justify-content:center;text-align: center;">
        <div class="pure-u">
            <h1 class="content-head">{{title}}</h1>
            <h2>{{description}}</h2>
        </div>
    </div>
</template>

<script>

export default {
    name: "Header",
    data() {
        return {
            title: "Debate Breaker",
            description: "determine the points needed to advance to outrounds at debating tournaments"
        }
    }
}
</script>
<style>
.content-head {
    font-weight: 400;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    margin: 2em 0 1em;
    color:white
}

h2 {
    color:#aaa;
    font-weight: 400;
    letter-spacing: 0.1em;
    margin: 2em 0 1em;
}
</style>