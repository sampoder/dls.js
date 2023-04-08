# 🏏 `dls.js`

A JS library for the Duckworth–Lewis–Stern method: https://en.wikipedia.org/wiki/Duckworth%E2%80%93Lewis%E2%80%93Stern_method. This library is based on the DLS table in [the ICC's guide to DLS](http://icc-live.s3.amazonaws.com/cms/media/about_docs/518a6ddb1aaf6-Duckworth_Lewis%20Method.pdf).

## Installation

The package is available as `@sampoder/dls.js` on [NPM](https://www.npmjs.com/package/@sampoder/dls.js) which after installation can be used like:

```js
const { DLS } = require('@sampoder/dls.js')
```

or 

```js
import { DLS } from '@sampoder/dls.js'
```

You can also import it directly from Skypack through URL imports:

```js
import { DLS } from 'https://cdn.skypack.dev/@sampoder/dls.js';
```

Make sure your script has the property `type="module"` set.

## The DLS Class

The `DLS()` class has the following properties:

| Property      |
| ----------- |
| `overs`: the amount of overs in the game if no interuptions occur, eg. 20 for a T20. Defaults to 50. |
| `G50`: the G50 value used if the first batting team's innings is interuptted. Defaults to 200. |
| `firstTeamScore` |
| `secondTeamScore` |
| `firstTeamWicketsLost` |
| `secondTeamWicketsLost` |
| `firstTeamOversRemaining` |
| `secondTeamOversRemaining` |
| `firstTeamOversPassed` |
| `secondTeamOversPassed` |

The `DLS()` class has the following methods:

| Method      | Description | Required Properties |
| ----------- | ----------- | ----------- |
| `getParScore()`  | `getParScore()` calculates the par score for a team chasing in the second. When the second innings is cut short, this score can be used to determine whether they've won or not. | `overs`, `firstTeamScore`, `secondTeamOversPassed` & `secondTeamWicketsLost` |
| `getRevisedTarget(oversLost)`   | `getRevisedTarget()` calculates a revised target for the chasing team when overs are lost in the second innings. | `overs`, `firstTeamScore`, `secondTeamOversPassed` & `secondTeamWicketsLost`  |
| `getRevisedTargetWhenFirstInningsCutShort()` | `getRevisedTargetWhenFirstInningsCutShort()` calculates a revised target for the chasing team when overs are lost in both the first innings and second innings - it should be ran at the end of the first innings and returns a target for the chasing team. | `G50`, `overs`,`firstTeamScore`, `firstTeamWicketsLost`, `firstTeamOversPassed` (this should be the amount of overs they got to bat in total) |
