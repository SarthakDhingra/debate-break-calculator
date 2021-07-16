# debate-break-calculator

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

## Overview
- Debating is an activity where teams argue against each other in favour or against a motion, for example "This House Would allow companies to buy the rights to govern economically failing cities". Thousands of debating tournaments are hosted every year with the largest tournaments boasting over a thousand participants.

- Debating tournaments consist of preliminary rounds and outrounds (e.g. quarterfinals). In preliminary rounds, teams are ranked by a panel of judges and awarded points for these rankings. After all preliminary rounds, teams with the highest amount of points advance, or "break", to outrounds. There is a lot of variation in the number of points needed advance to outrounds. With this in mind, Debate Breaker determines the best-case (lowest points needed) and worst-case (highest points needed) break scenarios based on a tournaments configuration.

## Notes
- The calculator assumes the tournament is using a bracketing system for each rounds draw. An explanation of the bracketing system can be found in the first paragraph of the following pdf: https://www.qsda.org/juniors/Juniors_Bracketing_System.pdf
- Things like team conflicts that alter the tournament draw may cause errors
- For a list of tournaments that the calculator has been tested on see ```test/Breaker.tests.js```. ```it.skip``` implies the calculator was incorrect for that tournament.

## TO DO
- Styling
    - On mobile add space between buttons
    - Change button colour after click
    - Add line to separate resulting text
- Edge Cases
    - All teams break
    - No guranteed break
- General
    - Modularize and clean up code


