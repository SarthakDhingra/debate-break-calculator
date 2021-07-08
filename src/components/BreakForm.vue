<template>
    
    <div class="pure-g" style="justify-content:center;text-align: center;">
        <div class="pure-u">
            <form class="pure-form pure-form-stacked" @submit.prevent="onSubmit($event)">
                <fieldset>
                    <label for="teams">teams</label>
                    <input type="number" id="teams" v-model.number="teams"/>
                    <br>
                    <label for="rounds">ROUNDS</label>
                    <input type="number" id="rounds" v-model.number="rounds">
                    <br>
                    <label for="breaking">BREAKING</label> 
                    <input type="number" id="breaking" v-model.number="breaking">
                    <br>
                    <label for="breaking">TEAMS PER ROUND</label> 
                    <button class="pure-button" name="style" value=2 type="submit" title="e.g. Australs">&nbsp;&nbsp;&nbsp;&nbsp;Two&nbsp;&nbsp;&nbsp;&nbsp;</button>
                    <button class="pure-button" name="style" value=4 type="submit" title="e.g. British Parliamentary">&nbsp;&nbsp;&nbsp;&nbsp;Four&nbsp;&nbsp;&nbsp;&nbsp;</button>
                </fieldset>
            </form>
        </div>
    </div>

    <br>
    <br>
    
    <div v-if="displayResults" style="justify-content:center;text-align: center;">
        <div class="pure-g">
            <div class="pure-u-1-2">
                <h3>Best Case</h3>
            </div>
            <div class="pure-u-1-2">
                <h3>Worst Case</h3>
            </div>
        </div>
        <div class="pure-g">
            <div class="pure-u-1-2">
                <h4>{{best_guranteed}}</h4>
                <h4>{{best_speaks}}</h4>
            </div>
            <div class="pure-u-1-2">
                <h4>{{worst_guranteed}}</h4>
                <h4>{{worst_speaks}}</h4>
            </div>
        </div>
    </div>

    <div v-if="error" style="justify-content:center;text-align: center;">
        <h3 style="color:red">Number of Breaking teams must be divisible by teams per round</h3>
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
            best_guranteed: '',
            best_speaks:'',
            worst_guranteed: '',
            worst_speaks:'',
            error: false
        }
    },
    methods: {
        onSubmit(event) {

            this.displayResults = true
            this.error = false
            let style = parseInt(event.submitter.attributes.value.value)

            // error validation
            if (this.breaking % style) {
                this.displayResults = false
                this.error = true
                return
            }

            // get results
            let tournament = new Tournament(style)
            let results = tournament.getBreak(this.teams, this.breaking, this.rounds)
            let best = results[0]
            let worst = results[1]

            // get strings
            this.best_guranteed = `all teams on ${best.guranteed_break} points will break`
            this.best_speaks = `${best.breaking_on_speaks} out of ${best.total_on_speaks} teams on ${best.speaks_break} points will break`
            this.worst_guranteed = `all teams on ${worst.guranteed_break} points will break`
            this.worst_speaks =  `${worst.breaking_on_speaks} out of ${worst.total_on_speaks} teams on ${worst.speaks_break} points will break`
            
        }
    }
}
</script>

<style>
label {
    color:white;
    font-weight: 400;
    text-transform: uppercase;
    letter-spacing: 0.1em;
}
.pure-button {
    margin: 5px;
    border-radius: 5px;
    font-weight: 400;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color:#2d3e50;
}

input {
    font-weight: 400;
    width:100%
}

h3 {
    color:white;
    font-weight: 400;
    text-transform: uppercase;
    letter-spacing: 0.1em;
}

h4 {
    color:white;
    font-weight: 400;
    letter-spacing: 0.1em;
    margin: 2em 0 1em;
}



</style>
