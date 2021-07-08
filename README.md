# debate-break-calculator

## Overview
- Debating is an increasingly popular activity where teams argue against each either in favour or against a motion (e.g. whether marijuana should be legalized). Thousands of debating tournaments are hosted every single year with the most recent Worlds Universities Debating Championships held in Thailand having over 1000 participants (https://wudc2020.herokuapp.com/wudc2020/)

- Typically debating tournaments consist of preliminary rounds and outrounds (e.g. quarterfinals or semifinals). In preliminary rounds, teams are ranked in comparison to other teams they debated against (determined by a panel of judges) and awarded points based off of their ranking. After preliminary rounds are over, teams with the highest amount of points advance, or "break", to outrounds. There can be a lot of variation in the number of points you need to advance to outrounds. With this in mind, Debate Break Calculator determines the best-case (lowest amount of points needed to break) and worst-case (highest amount of points needed to break) break scenarios based on the number of teams in the tournament, number of preliminary rounds, number of teams advancing to outrounds, and the style of debate

## Notes
- Style is the number of teams that are in one debate. For example British Parliamentary is 'Four Teams' while Canadian Parliamentary and Australs are 'Two Teams'
- The calculator assumes the tournament is using a bracketing system for each rounds draw. An explanation of the bracketing system can be found in the first paragraph of the following pdf: https://osdu.org/wp-content/uploads/2018/10/Bracketing_Scoring_System.pdf
- Things like team conflicts that alter the tournament draw may cause errors

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

### TO DO
- Edge Cases
    - All teams break
    - No guranteed break

- Testing
    - edge cases
    - Only one round
    - invalid input

