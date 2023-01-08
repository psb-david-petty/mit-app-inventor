# `APCSPStroopExample`

## About this app

The `APCSPStroopExample` app is described in the `Screen1.AboutScreen`.

> This app ​demonstrates '&hellip;the delay in reaction time between congruent and incongruent stimuli​' known as the <a href="https://en.wikipedia.org/wiki/Stroop_effect">Stroop Effect</a> &mdash; try​ to say the <strong>color</strong> of the word, not the word itself.​ <br><br>The app illustrates all aspects of the APCS-P requirements for the Create Performance Task:<br>• List storing and access used to manage the complexity of the program;<br>• A procedure w/ a parameter that is called from different places with different values and whose behavior varies based on the value of the parameter; and<br>• An algorithm that includes sequencing, selection, and repetition.

## Code

[![APCSPExample blocks](./APCSPStroopExample.png)](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPStroopExample/APCSPStroopExample.png)

- The *Reset* `Button` invokes the *reset* procedure, which invokes the *stroop* procedure to shuffle the color names and their colors.
- `Button1`, `Button2`, `Button3`, `Button4`, `Button5`, `Button6`, and `Button7` do nothing, but provide the canvas for the names and their colors.
- The *Matching* `Button` invokes the *stroop* procedure with a flag specifying that the word colors match the word names.
- The *Shuffled* `Button` invokes the *stroop* procedure with a flag specifying that the word colors *do not* match the word names.

## Scoring

Meeting the criteria for the APCS-P Create Performance Task [rubric](https://apcentral.collegeboard.org/media/pdf/ap22-sg-computer-science-principles.pdf) involves:

### Row 1

- The purpose of the program is to demonstrate the [Stroop Effect](https://en.wikipedia.org/wiki/Stroop_effect), '&hellip;the delay in reaction time between congruent and incongruent stimuli.' The classic experiment demonstrated by John Ridley Stroop in 1935 asks subjects to say the *color* of the text under two conditions: where the color matches the text and where the color does not match the text.
- The function of the program is to present the user with a shuffled list of color names with *matching* colors or a shuffled list of color names with *shuffled* colors so they can administer the Stroop test.
- The input of the program is clicking either of the two `Button`s &mdash; *Matching* or *Shuffle*. The output of the program is presenting the user with a shuffled list of color names with *matching* colors (when the *Matching* `Button` is clicked) or a shuffled list of color names with *shuffled* colors (when the *Shuffled* `Button` is clicked).

---

### Row 2

[![stroop blocks](./stroop-blocks.png){:width="800px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPStroopExample/stroop-blocks.png)


- The `nameIndexes` list is a local variable both *initialized* and *used* in the program code for the `stroop` procedure (above) to partially fulfill the programs purpose and to manage its complexity.
- In the program code for the `stroop` procedure (above), the `nameIndexes` list is *initialized* as a local variable by the *shuffle* procedure, shuffling a range of integers. In the program code for the `stroop` procedure (above), the `nameIndexes ` list is *used*, in turn, by the `shuffle` procedure to initialize another local variable (`colorIndexes`), shuffling the `nameIndexes` list. For example, because shuffling is random, the `stroop` procedure might generate the following 7-element lists:

| List | Index `1` | Index `2` | Index `3` | Index `4` | Index `5` | Index `6` | Index `7` |
| --- | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| **`rangeList`** | `1` | `2` | `3` | `4` | `5` | `6` | `7` |
| **`nameIndexes`** | `7` | `1` | `6` | `3` | `4` | `5` | `2` |
| **`colorIndexes`** | `6` | `7` | `2` | `4` | `5` | `3` | `1` |


- So as to not present the same Stroop test to the user every time, the `nameIndexes` list represents the shuffled names of colors. In the example, the `Button` at index `1` will have the color *name* at index `7` and the *color* at index `6`,  the `Button` at index `2` will have the color *name* at index `1` and the *color* at index `7`, *etc.* This assumes that the global `names` list and the global `colors` list (shown in the program code above) are parallel lists with corresponding elements.

---

### Row 3

[![stroop blocks](./shuffle-blocks.png){:width="800px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPStroopExample/shuffle-blocks.png)
[![stroop blocks](./swap-blocks.png){:width="400px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPStroopExample/swap-blocks.png)

-  In the program code for the `shuffle` procedure (above), the heart of [Satollo's Algorithm](https://en.wikipedia.org/wiki/Fisher%E2%80%93Yates_shuffle#Sattolo's_algorithm) is swapping elements of the list. This manages the complexity of the program code, because the alternative to the program code for the `swap` procedure (above), is to use a fixed number of (global) variables to achieve the same result. For example, even with *three* elements (global variables `element1`, `element2`, `element3`), the code for an example `swapVariables` procedure could be:

[![stroop blocks](./swapVariables-blocks.png){:width="400px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPStroopExample/swapVariables-blocks.png)

- This approach is *clearly* more complex even with only three variables, while a typical Stroop Test involves seven or more elements. Such a procedure would be proportionately more complex and would require code changes for every added element, whereas adding to the global `names` and the global `colors` parallel lists would not require program changes.

---

### Row 4

-  **Row 4** &mdash; [![color blocks](./color.png){:width="400px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/color.png) [![Button1 blocks](./Button1.png){:width="200px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/Button1.png) The *color* procedure has a single *number* parameter which is set when it is called from each of the `Button.Clicked` handlers. **Note**: *The function of this program is trivial, so the contribution to the overall functionality of the program is also trivial.*

---

### Row 5

-  **Row 5** &mdash; [![color blocks](./color.png){:width="400px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/color.png) The *color* procedure initializes the `Button.BackgroundColor`s of *all* buttons by iterating through the `buttons` list setting the `Button.BackgroundColor` of each `Button` in turn. The rest of the sequence of blocks in the *color* procedure consists of a series of selections that test the value of the `number` parameter and react differently (set the `Button.BackgroundColor` of a differnt `Button`) based on its value.

---

### Row 6

-  **Row 6** &mdash; [![Button1 blocks](./Button1.png){:width="200px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/Button1.png) [![Button2 blocks](./Button2.png){:width="200px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/Button2.png) In each call to the *color* procedure the *number* parameter is given a different value. The result of the call to [![color1 blocks](./color1.png){:width="200px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/color1.png) is to change the `Button.BackgroundColor` of `Button1`.  The result of the call to [![color2 blocks](./color2.png){:width="200px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/color2.png) is to change the `Button.BackgroundColor` of `Button2`. **Note**: *The function of this program is trivial, so the result of each call to the selected procedure is also trivial.*

## Designer

All components retain their default properties, &mdash; except `Width` and `Height` set to `Fill parent...` where necessary to center UX components, `Button` text(s) changed from their defaults(s), and `Screen1.AboutScreen` set to the explanatory text (above).

<hr>

[&#128279; permalink](https://psb-david-petty.github.io/mit-app-inventor/APCSPStroopExample/), [&#128297; repository](https://github.com/psb-david-petty/mit-app-inventor/tree/master/APCSPStroopExample), and [![MIT AI2 logo](../mit-app-inventor-2-logo-200x200.png){:width="36px"} `.AIA`](https://psb-david-petty.github.io/mit-app-inventor/APCSPStroopExample/APCSPStroopExample) for this page.
