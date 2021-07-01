<template>
    
    <div class="pure-g" style="justify-content:center;text-align: center;">
        <div class="pure-u">
            <form class="pure-form pure-form-stacked" @submit.prevent="onSubmit($event)">
                <fieldset>
                    <label for="teams">TEAMS</label>
                    <input id="teams" v-model.number="teams">
                    <br>
                    <label for="rounds">ROUNDS</label>
                    <input id="rounds" v-model.number="rounds">
                    <br>
                    <label for="breaking">BREAKING</label> 
                    <input id="breaking" v-model.number="breaking">
                    <br>
                    <br>
                    <button name="style" value=2 type="submit">Two Teams</button>
                    <button name="style" value=4 type="submit">Four Teams</button>
                </fieldset>
            </form>
        </div>
    </div>
    


    <div v-if="displayResults" style="justify-content:center;text-align: center;">
        <div class="pure-g">
            <div class="pure-u-1-2">
                <p>Best Case</p>
            </div>
            <div class="pure-u-1-2">
                <p>Worst Case</p>
            </div>
        </div>
        <div class="pure-g">
            <div class="pure-u-1-2">
                <p>{{best_string}}</p>
            </div>
            <div class="pure-u-1-2">
                <p>{{worst_string}}</p>
            </div>
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