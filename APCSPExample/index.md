# `APCSPExample`

## About this app

The `APCSPExample` app is described in the `Screen1.AboutScreen`.

> This trivial app illustrates all aspects of the APCS-P requirements for the Create Performance Task:<br>• List storing and access used to manage the complexity of the program;<br>• A procedure w/ a parameter that is called from different places with different values and whose behavior varies based on the value of the parameter; and<br>• An algorithm that includes sequencing, selection, and repetition.

## Code

[![APCSPExample blocks](./APCSPExample.png)](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/APCSPExample.png)

- The *Reset* `Button` invokes the *reset* procedure, which initializes all the `Button.BackgroundColor`s.
- `Button1`, `Button2`, and `Button3` invoke the *color* procedure to (a) initialize the `Button.BackgroundColor`s and (b) change the `Button.BackgroundColor` for *that* `Button`.

Meeting the criteria for the APCS-P Create Performance Task [rubric](https://apcentral.collegeboard.org/pdf/ap-computer-science-principles-2021-create-performance-task-scoring-guidelines.pdf) involves:

<ol start="2">
<li>The `buttons` list is initialized in a global variable. The `buttons` list is used in the *color* procedure to initialize the `Button.BackgroundColor`s of all buttons any time *any* button is clicked.</li>
<li>Storing the `Button` components in a list facilitates the adding of additional `Button` components with additional functionality by making minimal changes to the code.</li>
<li>[![color blocks](./color.png)](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/color.png) [![Button1 blocks](./Button1.png)](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/Button1.png) The *color* procedure has a single *number* parameter which is set when it is called from each of the `Button.Clicked` handlers. **Note**: *The function of this program is trivial, so the contribution to the overall functionality of the program is also trivial.*</li>
<li>[![color blocks](./color.png)](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/color.png) The *color* procedure initializes the `Button.BackgroundColor`s of *all* buttons by iterating through the `buttons` list setting the each of the `Button.BackgroundColor` of each `Button` in turn. The rest of the sequence of blocks in the *color* procedure consists of a series of selections that test the value of the `number` parameter and react differently (set the `Button.BackgroundColor` of a differnt `Button`) based on its value.</li>
<li>[![Button1 blocks](./Button1.png)](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/Button1.png) [![Button2 blocks](./Button2.png)](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/Button2.png) In each call to the *color* procedure the *number* parameter is given a different value. The result of call to [![color1 blocks](./color1.png)](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/color1.png) is to change the `Button.BackgroundColor` of `Button1`.  The result of call to [![color2 blocks](./color2.png)](https://github.com/psb-david-petty/mit-app-inventor/blob/master/APCSPExample/color2.png) is to change the `Button.BackgroundColor` of `Button2`. **Note**: *The function of this program is trivial, so the result of each call to the selected procedure is also trivial.*</li>
</ol>

## Designer

All components retain their default properties, &mdash; except `Width` and `Height` set to `Fill parent...` where necessary to center UX components, `Button` text(s) changed from their defaults(s), and `Screen1.AboutScreen` set to the explanatory text (above).

<hr>

[&#128279; permalink](https://psb-david-petty.github.io/mit-app-inventor/APCSPExample/) and [&#128297; repository](https://github.com/psb-david-petty/mit-app-inventor/tree/master/APCSPExample) for this page.
