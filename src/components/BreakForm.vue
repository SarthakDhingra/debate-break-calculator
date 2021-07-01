<template>
    <div class="columns has-text-centered" >
        <div class="column"></div>
        <div class="column">

            <form class="pure-form pure-form-stacked splash-subhead" @submit.prevent="onSubmit($event)">
                <label class="label" for="teams" style="color:white">TEAMS</label>
                <input class="input" id="teams" v-model.number="teams">
                <br>
                <br>
                <label class="label" for="rounds" style="color:white">ROUNDS</label>
                <input class="input" id="rounds" v-model.number="rounds">
                <br>
                <br>
                <label class="label" for="breaking" style="color:white">BREAKING</label> 
                <input class="input" id="breaking" v-model.number="breaking">
                <br>
                <br>
                <button class="button" name="style" value=2 type="submit">Two Teams</button>
                <button class="button" name="style" value=4 type="submit">Four Teams</button> 
            </form>

        </div> 
        <div class="column"></div>
    </div>

    <div v-if="displayResults">
        <div class="columns is-mobile has-text-centered">
            <p class="column">Best Case</p>
            <p class="column">Worst Case</p>
        </div>
        <div class="columns is-mobile has-text-centered">
            <p class="column">{{best_string}}</p>
            <p class="column">{{worst_string}}</p>
        </div>
    </div>
</template>

<script>

import { Tournament } from './../mixins/Breaker.js'

export default {
    name: "BreakForm",
    data() {
        return {
            teams: 40,
            rounds: 5,
            breaking: 8,
            displayResults: false,
            best_string: 'best',
            worst_string: 'worst'
        }
    },
    methods: {
        onSubmit(event) {

            let style = parseInt(event.submitter.attributes.value.value)
            let tournament = new Tournament(style)
            let results = tournament.getBreak(this.teams, this.breaking, this.rounds)

            let best = results[0]
            let worst = results[1]

            this.best_string = `All teams on ${best.guranteed_break} points will break. ${best.breaking_on_speaks} out of ${best.total_on_speaks} teams on ${best.speaks_break} points will break`
            this.worst_string = `All teams on ${worst.guranteed_break} points will break. ${worst.breaking_on_speaks} out of ${worst.total_on_speaks} teams on ${worst.speaks_break} points will break`
            this.displayResults = true
        }
    }
}
</script>

<style>
    p {
        color:white
    }
</style>