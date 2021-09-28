<script type="text/javascript" src="/twistysim.js"></script>
<style type="text/css" rel="stylesheet">
/* modifies the opacity of the cube wireframe */
.ttk-shp-poly {
    stroke-opacity: 0.3;
}
</style>

# CMLL

## Objective

The goal of CMLL (Corners of the Last Layer, in essence) is to solve the corners on the `U` layer — both oriented (all yellow on top) and permuted (all the facelets on the side of the corners are completely solved relative to each other) as shown in the figure below.

<div id="inf1">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wtwwtwwtwgggggggtgrtrrtrrtrytytttytybbbbbbbtbotootooto')
    ('#inf1');
</script>
</div>

This step will be separated into 2 steps, both of which need 1 algorithm each.

## Orienting the corners

<div id="orient">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wtwwtwwtwggggggltlrtrrtrltlytytttytybbbbbbltlotootoltl')
    ('#orient');
</script>
</div>

In this step, all you need to worry about are the **yellow** facelets — the side colours (marked in gray) do not matter. 

For this step, using the `sune` algorithm (sometimes multiple times) will be able to orient the corners. 

<div id="SUNE">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wtwwtwwtwggggggltlrtrrtrltlytytttytybbbbbbltlotootoltl')
    .case(`R U R' U R U2 R'`)
    ('#SUNE');
</script>

One way to learn the algorithm is to think of taking the pair out with `R U R'`, then setting up to another insertion with a `U` move, then inserting the last pair by doing `R U2 R'`.

For a more visual representation:

Applying `R U R'` takes the pair out,

<div id="rur">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wtwwtwwtwggggggltlrtrrtrltlltltttltlbbbbbbltlotootoltl')
    .alg(`R U R'`)
    ('#rur');
</script>

And inserting with `R U2 R'` puts the pair back in through another insertion.

<div id="ru2r">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wtwwtwwtwggggggltlrtrrtrltlltltttltlbbbbbbltlotootoltl')
    .case(`R U2 R'`)
    ('#ru2r');
</script>

So all that needs to be linked together is to just do one extra setup move in between the two cases and you have learned the algorithm.

It's also reasonable to learn this by muscle memory/brute force, but I highly recommend trying to think of it as pair insertions, especially because it is easier to remember in the long term.

If you look at the first visual though, the algorithm twists all but the bottom left corner clockwise, which means that your end goal in this step is to end up with **only 1 corner oriented**, from which you can then apply the `sune` algorithm either once or twice (depending on whether the corners need to be twisted counter-clockwise or clockwise) to orient all the corners.

How do we get there then? One approach would be to check all `4` different possibilities and see which one leads to you having just `1` oriented corner in total. Let's take a look at some examples:

In the visual below, you can move the cube by a `U` move by pressing the forward and backward buttons.

<div id="L">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wtwwtwwtwggggggltlrtrrtrltlytytttytybbbbbbltlotootoltl')
    .case(`U R U R' U' R' F R F'`)
    .alg(`U U U`)
    .showAlg(false)
    ('#L');
</script>

For our first angle, imagine twisting all the corners but the bottom left one clockwise: what you see is that the bottom right corner twists such that yellow is facing you, the top right corner twists such that it's facing away from you, and the top left corner twists such that it's facing leftwards. As a result, no corners are oriented, which means we do not want to execute `sune` from this angle.

From the second angle, imagine the same process - the bottom right corner ends up facing right, the top right corner ends up facing away from you, and the top left corner ends up facing upwards. In sum, we only have 1 oriented corner in this step, which means that this is the angle to execute `sune` from.

For completion’s sake, I'll also go through the process for the other two angles.

From the third angle, the bottom left corner faces right, the top right corner faces up, and the top left corner faces away from you — in sum, we have 2 oriented edges, so this is not the correct angle.

From the fourth angle, the bottom right corner faces up, the top right corner faces right, and the top left corner faces left — in sum we have 2 oriented edges once again.

---

After getting only one corner oriented, all that you need to do is put the oriented corner in the bottom left, then apply the `sune` algorithm again. For example if we do `sune` from the angle shown in the visual below, the bottom right corner will be facing us, the top right corner will face right, and the top left corner will face away from us. From this, there will still only be a total of 1 corner oriented, which means we can then apply the same algorithm from a different angle to solve corner orientation.

<div id="S2">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wtwwtwwtwggggggltlrtrrtrltlytytttytybbbbbbltlotootoltl')
    .case(`U2 R U2 R' U' R U' R'`)
    .alg(`R U R' U R U2 R'`)
    ('#S2');
</script>

Notice how after the algorithm is done, there is still only 1 corner oriented? From there, we can then apply `sune` again after moving the `U` layer such that we have the 1 oriented corner in the bottom left.

<div id="S1">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wtwwtwwtwggggggltlrtrrtrltlytytttytybbbbbbltlotootoltl')
    .case(`U2 R U R' U R U2 R'`)
    ('#S1');
</script>

---

A more formulaic approach to the step above would be to follow this image (from [Cubeskills](https://www.cubeskills.com/uploads/pdf/tutorials/the-beginners-method-for-solving-the-rubiks-cube.pdf))

![image](https://i.imgur.com/IIYopnA.png)

It is highly recommended learning using the other method though — it makes the step after CMLL easier to grasp due to having very similar concepts.

## Permuting the Corners

After the corners are oriented, we can finally deal with permuting them. What this step entails is memorizing another (slightly longer) algorithm — however, there are fewer cases and by extension, mental gymnastics to deal with. 

The algorithm is `R U R' U' R' F R2 U' R' U' R U R' F'` as seen in the visual below:

<div id="t">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wtwwtwwtwgggggggtgrtrrtrrtrytytttytybbbbbbbtbotootooto')
    .case(`R U R' U' R' F R2 U' R' U' R U R' F'`)
    ('#t');
</script>

What it does is swaps the two corners on the right with each other, while preserving the solved 'headlights' on the left side of the cube. If you look at the blue stickers in the visual, you notice that they are both on the same face? That's what's called `headlights`.

In general, you can just find the `headlights`, then do `U` moves until the headlights are on the left, and then do the algorithm for permuting the corners.

**If you do not see any headlights**, simply just do the algorithm, and you will then see headlights appear. If you want, you can trace why that works by looking at swapping any 2 pieces, but this isn't particularly important. 