# Nouveaux dessins géométriques et artistiques avec votre micro-ordinateur

👉 [https://editor.p5js.org/v3ga/collections/ALPCSgG3E](https://editor.p5js.org/v3ga/collections/Q6wJic-1k)

This repository presents programs written by french mathematician and computer scientist [Jean-Paul Delahaye](https://fr.wikipedia.org/wiki/Jean-Paul_Delahaye) in the book *"Nouveaux dessins géométriques et artistiques avec votre micro-ordinateur"* published in 1985 for the [Eyrolles](https://www.eyrolles.com/) french publishing house.<br />

The programs were originally programmed with Microsoft Basic for [Canon X-07](https://en.wikipedia.org/wiki/Canon_X-07) computer, outputs were drawn on a [Canon X710 plotter](http://pocket.free.fr/html/canon/x-710_f.html). They were recoded with [p5.js](https://p5js.org/), the online collection can be found [here](https://editor.p5js.org/v3ga/collections/ALPCSgG3E). You can click on each thumb to jump to the corresponding sketch. Be sure to edit the *DESSIN* variable in the program header.

I contacted Jean-Paul Delahaye who gave me access to links for downloading scans of the two editions of “Dessins géométriques”. He kindly allowed me to share them.<br />
👉 [Dessins géométriques et artistiques avec votre micro-ordinateur](https://nextcloud.univ-lille.fr/index.php/s/R4PgSRWGyHEbDgG)<br />
👉 [Nouveaux dessins géométriques et artistiques avec votre micro-ordinateur](https://nextcloud.univ-lille.fr/index.php/s/cwXAAokbbeaykW6)

👉 You can find the recoded sketches of the first book *"Dessins géométriques et artistiques avec votre micro-ordinateur"* here : https://github.com/v3ga/dessins_geometriques_et_artistiques

## Library
I tried to be as close as possible as the original syntax, thus I developed a parser that interprets the string generated by *LPRINT* commands.<br />The [library](https://www.v3ga.net/dessins_geometriques/init_trace.js) contains the following command : 
| Command | Description |
| --- | --- |
| `INIT` | set up the canvas with an initial size of 500x500 pixels, accepts `{svg:true}` as parameter to export to vector format  |
| `INIT2(height)` | set up the canvas with the width equal to 500 pixels and a custom height, accepts `{svg:true}` as parameter to export to vector format |
| `INIT_WH(width,height)` | set up the canvas with custom width and height, accepts `{svg:true}` as parameter to export to vector format |
| `LPRINT(s)` | concatenates `s` to the `OUTPUT` global variable used by `TRACE()`for drawing  |
| `TRACE()` | draw the output using [beginShape](https://p5js.org/reference/#/p5/beginShape) / [vertex](https://p5js.org/reference/#/p5/vertex) / [endShape](https://p5js.org/reference/#/p5/beginShape) commands by interpretating the string generated by `LPRINT` calls|
| `TRACE2()` | draw the output, [endShape](https://p5js.org/reference/#/p5/beginShape) is not used with [CLOSE](https://p5js.org/reference/#/p5/CLOSE) parameter  |
| `PALETTE(which)` | sets the palette, use `RED`,`YELLOW` or `GREEN` as parameter. Defaults otherwise to grey background and black stroke   |

Some sketches were added a [translate](https://p5js.org/reference/#/p5/translate) command to center the drawing as it happened sometimes it was out of canvas bounds.

### Example
```js
let DESSIN = 30;
let NP=480,PI=Math.PI;
let N=400;

function setup() 
{
  INIT();
  
  for (let I = 0; I < N; I++) {
    let X = R*cos(A), Y= R*sin(A);
    let X_ = int(NP/2*(1+X)), Y_ = int(NP/2*(1+Y));
    if (I == 0) LPRINT(`M${X_},${Y_}`);
    if (I > 0) LPRINT(`D${X_},${Y_}`);
  }

  TRACE2();
}
```
## Summary
- [3. Courbes en coordonnées polaires](#3-courbes-coordonnées-polaires)


