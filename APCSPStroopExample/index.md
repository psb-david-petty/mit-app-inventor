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
- In the program code for the `stroop` procedure (above), the `nameIndexes` list is *initialized* as a local variable by the `shuffle` procedure, shuffling a range of integers. In the program code for the `stroop` procedure (above), the `nameIndexes ` list is *used*, in turn, by the `stroop` procedure to initialize another local variable (`colorIndexes`), shuffling a copy of the `nameIndexes` list if the `shuffle?` parameter is `true`. For example, because shuffling is random, the `stroop` procedure might generate the following 7-element lists:

| List | Index `1` | Index `2` | Index `3` | Index `4` | Index `5` | Index `6` | Index `7` |
| --- | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| **`rangeList`** | `1` | `2` | `3` | `4` | `5` | `6` | `7` |
| **`nameIndexes`** | `7` | `1` | `6` | `3` | `4` | `5` | `2` |
| **`colorIndexes`** | `6` | `7` | `2` | `4` | `5` | `3` | `1` |


- So as to not present the same Stroop test to the user every time, the `nameIndexes` list represents the shuffled names of colors and the `colorIndexes` list (which is the shuffled `nameIndexes` list when the `shuffle?` parameter is `true`) represents the colors of the names. In the example, the `Button` at index `1` will have the color *name* at index `7` and the *color* at index `6`,  the `Button` at index `2` will have the color *name* at index `1` and the *color* at index `7`, *etc.* This assumes that the global `names` list and the global `colors` list (shown in the program code above) are parallel lists with corresponding elements.

---

### Row 3

[![shuffle blocks](./shuffle-blocks.png){:width="800px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPStroopExample/shuffle-blocks.png)
[![swap blocks](./swap-blocks.png){:width="400px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPStroopExample/swap-blocks.png)

-  In the program code for the `shuffle` procedure (above), the heart of [Satollo's Algorithm](https://en.wikipedia.org/wiki/Fisher–Yates_shuffle#Sattolo's_algorithm) is in swapping the elements of the list(s). This manages the complexity of the program code, because the alternative to the program code for the `swap` procedure (above), is to use a fixed number of (global) variables to achieve the same result. For example, even with only *three* elements (global variables `element1`, `element2`, `element3`), the code for an example `swapVariables` procedure could be:

[![swapVariables blocks](./swapVariables-blocks.png){:width="400px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPStroopExample/swapVariables-blocks.png)

- This approach is *clearly* more complex even with only three variables, while a typical Stroop Test involves seven or more elements. Such a procedure would be quadratically more complex and would require code changes for every added element, whereas adding to the global `names` and the global `colors` parallel lists would not require any program code changes.

---

### Row 4

[![stroop blocks](./stroop-blocks.png){:width="800px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPStroopExample/stroop-blocks.png)

- The `stroop` procedure (above) is a student-developed procedure with at least one parameter that has an effect on the functionality of the procedure. The parameter `shuffle?` is a Boolean value that determines whether the `colorIndexes` local variable list is a shuffled copy of the `nameIndexes` local variable list or whether the `colorIndexes` local variable list is a reference to the `nameIndexes` parameter and not shuffled relative to it.

[![ButtonMatching.Click blocks](./ButtonMatching.Click-blocks.png){:width="400px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPStroopExample/ButtonMatching.Click-blocks.png) [![ButtonShuffled.Click blocks](./ButtonShuffled.Click-blocks.png){:width="400px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPStroopExample/ButtonShuffled.Click-blocks.png)

- The `ButtonMatching.Click` event (above) shows where the student-developed procedure (`stroop`) is called with a `false` parameter &mdash; so the color *names* match the *colors*. The `ButtonShuffled.Click` event (above) shows where the student-developed procedure (`stroop`) is called with a `true` parameter &mdash; so the color *names* do not match the *colors*. 

---

### Row 5

[![stroop blocks](./stroop-blocks.png){:width="800px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPStroopExample/stroop-blocks.png)

- The `stroop` procedure (above) is a student-developed algorithm that includes sequencing (more than one program block), selection (an `if / else` block that either shuffles or does not shuffle the `nameIndexes` local variable list), and iteration (a `for each` counted loop that sets the properties of `Button`s in the global variable `buttons` list.
- To set up a Stroop Test, the student-developed algorithm works as follows:
 - Given three global-variable, fixed, parallel lists with corresponding elements. The lists are: `buttons` (containing references to the buttons whose text and text colors are to be modified), `names` (containing color names), and `colors` (containing colors corresponding to the color names).
 - Create two lists corresponding to the *indexes* of the `names` and `colors` lists. The `nameIndexes` list (the *indexes* of the `names` list) is shuffled relative to the indexes in order. The `colorIndexes` list (the *indexes* of the `colors` list) is either shuffled relative to the `nameIndexes` list (in the *shuffled* Stroop Test) or not shuffled relative to the `nameIndexes` list (in the *matching* Stroop Test).
 - Iterate through the `buttons` list, setting the *text* for each button to the name referred to in the `names` list indexed indirectly by the index in the corresponding position in the `nameIndexes` list and setting the *color* for each button to the color referred to in the `colors` list indexed indirectly by the index in the corresponding position in the `colorIndexes` list.
 - The `shuffle` procedure is a version of [Satollo's Algorithm](https://en.wikipedia.org/wiki/Fisher–Yates_shuffle#Sattolo's_algorithm) that shuffles lists in place.

---

### Row 6

-  **Row 6** &mdash; [![Button1 blocks](./Button1.png){:width="200px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/Button1.png) [![Button2 blocks](./Button2.png){:width="200px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/Button2.png) In each call to the *color* procedure the *number* parameter is given a different value. The result of the call to [![color1 blocks](./color1.png){:width="200px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/color1.png) is to change the `Button.BackgroundColor` of `Button1`.  The result of the call to [![color2 blocks](./color2.png){:width="200px"}](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/color2.png) is to change the `Button.BackgroundColor` of `Button2`. **Note**: *The function of this program is trivial, so the result of each call to the selected procedure is also trivial.*

## Designer

All components retain their default properties, &mdash; except `Width` and `Height` set to `Fill parent...` where necessary to center UX components, `Button` text(s) changed from their defaults(s), and `Screen1.AboutScreen` set to the explanatory text (above).

<hr>

[&#128279; permalink](https://psb-david-petty.github.io/mit-app-inventor/APCSPStroopExample/), [&#128297; repository](https://github.com/psb-david-petty/mit-app-inventor/tree/master/APCSPStroopExample), and [![MIT AI2 logo](../mit-app-inventor-2-logo-200x200.png){:width="36px"} `.AIA`](https://psb-david-petty.github.io/mit-app-inventor/APCSPStroopExample/APCSPStroopExample) for this page.
