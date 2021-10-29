<script type="text/javascript" src="/twistysim.js"></script>
<style type="text/css" rel="stylesheet">
/* modifies the opacity of the cube wireframe */
.ttk-shp-poly {
    stroke-opacity: 0.3;
}
</style>

# LSE

## Objective

In this step, the goal is to solve the last six edges, which will actually end up solving the entire cube!

## Edge Orientation (EO)

The first 'step' of LSE is to orient all the edges — making the white and yellow edges face either upwards or downwards. The colours on the other side of the edge does not matter for this step.

<div id="eo">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwggggggglgrlrrrrrlryyyyyyyyybbbbbbblbolooooolo')
    .case(`M2 U2 M U2 M U' M2 U M2 U M' U2 M'`)
    ('#eo');
</script>
</div>

**Make sure you have either the white center or the yellow center on the U layer!** Correct edge orientation depends on this being the case — if it isn't, the remaining steps are going to not behave as normal as the edges aren't going to be oriented *relative to the centers*.

Type | Description
:-- | :--
Oriented Edge/Good Edge | Edge where the white/yellow sticker is facing either upwards or downwards.
Misoriented Edge/Bad Edge | Edge where the white/yellow sticker is **not** facing either upwards or downwards.

In this step, we only need to use `M` and `U` moves - no other moves are needed.

There are still a few things we need to learn to make solving the rest of the cube easier:

### Solving the 'arrow' case

If you have 3 misoriented edges on the `U` layer and 1 misoriented edge on the `D` layer, you have an `arrow`. Looking at the misoriented edges on the `U` layer, you can sort of see a `V` shape which looks like an arrow. To get from this case to all edges oriented, you need to do the following steps:

1. Bring the tip of the `V` on the `U` layer above the misoriented edge on the `D` layer. We will call the edge representing the tip of the arrow and the misoriented edge on the `D` layer the 'edges in question'
2. Bring both of the edges in question to the `U` layer by either doing `M` or `M'`
3. Do either `U` or `U'` (does not make a difference)
4. Do an `M` move **in the opposite direction** of what you did in step 2.


<div id="frontarrow">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwggggggglgrlrrrrrlryyyyyyyyybbbbbbblbolooooolo')
    .case(`U M' U M`)
    ('#frontarrow');
</script>
</div>

<div id="backarrow">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwggggggglgrlrrrrrlryyyyyyyyybbbbbbblbolooooolo')
    .case(`U' M U M'`)
    ('#backarrow');
</script>
</div>

This turns a case from having `4` misoriented edges to having none of the edges misoriented.

Another extremely important concept in this step is an algorithm that *swaps* one of the edges in the `U` layer with one of the edges in the `D` layer while preserving our edge orientation. We'll call this the swapping algorithm.

> This can either be done by swapping the front two edges or the back two edges

To do this, we do the following steps:

1. Bring the edge in the `U` layer that we want to swap above the edge in the `D` layer that we want swapped.
2. Do either `M` or `M'` to bring them both to the `U` layer
3. Do a `U2`
4. Do an `M` move **in the opposite direction** of what you did in step 2.

Notice how the steps are extremely similar to the `arrow` case from earlier? If you try to remember these two cases as one larger case, you'll have an easier time memorizing these cases.

<div id="frontmu2m">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`M' U2 M`)
    ('#frontmu2m');
</script>
</div>

<div id="backmu2m">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`M U2 M'`)
    ('#backmu2m');
</script>
</div>

After you know both these cases, you can finally move onto solving edge orientation!

---

### Flowchart Approach

This approach requires more memorization than the intuitive approach below, but is still not a lot of pure memorization --- it's possible to brute force solve this step if you're stuck unlike the CMLL step from earlier.

In the visual below, the red coloured edges represent **misoriented** edges. In some of the visuals, you may not be able to see all the misoriented edges, but one feature of the cube is that there can only be an even number of misoriented and oriented edges in sum. 

All these cases lead to the `arrow`, which you can then solve intuitively from there.

![](https://i.imgur.com/97lzRoZ.png)

Remember that `M` moves follow the direction of `L` moves rather than `R` moves - this is a bit weird but because it's conventional, that's the way its done now.

### Intuitive Approach

The general way to get to all edges oriented is to set up to an `arrow` case, where there are three misoriented edges on the top layer, and one misoriented edge on the bottom layer. With this method, we will need just the arrow and the swapping algorithms and a bit of counting.

We want to end up with `4` misoriented edges in total, which means we want to do the arrow alg in a position where we will eventually end up with 4 misoriented edges.

<div id="frontmu2m1">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`M' U2 M`)
    ('#frontmu2m1');
</script>
</div>

If you look at the front two edges (yellow-red and yellow-white edges), you can see that by doing `M' U2 M`, they swap positions.

<div id="frontmu2mmisoriented">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`U' M U M'`)
    .alg(`M' U2 M`)
    ('#frontmu2mmisoriented');
</script>
</div>

Notice how after doing `M' U2 M` on the cube, the visual goes from having 3 misoriented edges on the top layer and 1 misoriented edge on the bottom layer to having 2 on top and 2 on bottom. In the example above, the red-white and orange-yellow edges swap position.

You can also do the swapping 'algorithm' from the back similarly to the arrow case.

<div id="backmu2m1">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`M U2 M'`)
    ('#backmu2m1');
</script>
</div>

---

### Example 1:

Knowing this information, let's try our hand at some LSE cases:

<div id="case1-1">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`U M U M U M' U M`)
    .alg(`U' U' U'`)
    .showAlg(false)
    ('#case1-1');
</script>
</div>

First, check to see how many misoriented edges there are — 2.

> Hint: the number of misoriented edges will ALWAYS be an even number; likewise for oriented edges.

Then, remember that your goal is to do the arrow alg such that you can get to 4 misoriented edges in total. If you remember what edges the arrow cases flip, you can basically check to see what your end case will become.

From the first angle in the visual, if you do an arrow in the front, you will end up flipping two oriented edges and two misoriented edges, leaving you with a total of two misoriented edges, which means that it isn't the correct angle. **However**, if you do an arrow from the back, you flip one misoriented edge and three oriented edges, which in total leads to four misoriented edges if you include the misoriented edge that does not get affected in the front.

From the second angle, doing the arrow in the front leads to two misoriented edges, and doing it from the back leads to six misoriented edges, so we can ignore this angle.

The third angle is just a mirror of the first angle, so the same thing applies (just see for yourself).

In the fourth angle, if you do an arrow in the front, you end up flipping one misoriented edge and three oriented edges, leaving you with four misoriented edges in total. If you do an arrow in the back, you end also end up flipping one misoriented edge and three oriented edges, leaving you with four in total too.

After executing the arrow alg from the correct angle (in this case, `M U' M'`), we get the case in the visual below:

<div id="case1-2">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`U M U M U M' U M`)
    .alg(`M U' M'`)
    ('#case1-2');
</script>
</div>

Notice how there are **four** bad edges in total, however we don't have the arrow case directly because we have two misoriented on the top, and two on the bottom, so we will have to do some swaps in order to set up to an arrow. In this case, we want to swap one of the oriented edges on the `U` layer with one of the misoriented edges on the `D` layer.

In the example below, the back two edges will be swapped, leading to an arrow case, which from there can lead to finishing EO.

<div id="case1-3">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`M U M' U M U M U M' U M`)
    .alg(`M U2 M' U2 M' U M`)
    ('#case1-3');
</script>
</div>

Doing `M U2 M'` swaps the back two, making an arrow case. From there, `U2` sets up to the correct angle for the arrow case, from which `M' U M` solves the arrow case fully.

### Example 2:

<div id="case2-1">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`R U' r' U' M' U r U r'`)
    .alg(`U' U' U'`)
    .showAlg(false)
    ('#case2-1');
</script>
</div>

In this case, we start off with all the edges misoriented. You can do the arrow from any angle here, because no matter what `U` move you do, you still have the same six misoriented edges.

<div id="case2-2">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`R U' r' U' M' U r U r'`)
    .alg(`M' U M`)
    ('#case2-2');
</script>
</div>

From here, we have one misoriented on top and one misoriented on bottom, which is the same as the example shown earlier. From here you can just follow the same steps as Example 1.

<div id="case2-3">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`M' U' M R U' r' U' M' U r U r'`)
    .alg(`U2 M U M'`)
    ('#case2-3');
</script>
</div>

Setup to arrow, then


<div id="case2-4">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`M U' M' U2 M' U' M R U' r' U' M' U r U r'`)
    .alg(`U M U M'`)
    ('#case2-4');
</script>
</div>

solve EO!

---

## Solving the Left and Right edges 

In this step, the aim is to solve the edges that are part of the left and right sides of the cube. Due to the fact that we always start with the blue-white first block, this means that the edges in question are the green-yellow and blue-yellow edges. 

The simplest, and typically most efficient, approach is to put both the green-yellow and blue-yellow edges on the bottom layer, then doing an `M2` from the correct angle to solve the edges.

<div id="ulur1">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`M' U2 M U M U2 M' M2 U2 M U2 M U' M2 U2 M2 U M' U2 M' U M2 U M' U2 M' U2 M U2 M'`)
    .alg(`M' U2 M`)
    ('#ulur1');
</script>
</div>

For example, you can do `M' U2 M` (front swap) here to bring the green-yellow edge to the `D` layer in the front.

<div id="ulur2">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`M' U2 M U M U2 M' M2 U2 M U2 M U' M2 U2 M2 U M' U2 M' U M2 U M' U2 M' U2 M U2 M'`)
    .alg(`M' U2 M`)
    ('#ulur2');
</script>
</div>

Afterwards, `U M U2 M'` (setup to back swap) will put the blue-yellow edge to the `D` layer in the back such that both of the edges in question are located in the `D` layer:

<div id="ulur3">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`U M U2 M' M2 U2 M U2 M U' M2 U2 M2 U M' U2 M' U M2 U M' U2 M' U2 M U2 M'`)
    .alg(`U M U2 M'`)
    ('#ulur3');
</script>
</div>

After you get both of the edges onto the bottom layer, all that's left is to move the corners with `U` moves until doing an `M2` will solve the edges relative to their corners.

In this case, `U'` will move the corners to the correct position:

<div id="ulur4">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`M U2 M' U' U M U2 M' M2 U2 M U2 M U' M2 U2 M2 U M' U2 M' U M2 U M' U2 M' U2 M U2 M'`)
    .alg(`U' M2'`)
    ('#ulur4');
</script>
</div>

---

Small shortcut: you can actually do an `M2` to insert the first edge onto the `D` layer as long as your other edge isn't there. However, if you can't grasp this, stick with just doing the swapping algorithm for now.

## Finishing the rest of the cube

You're nearly there!

Due to the properties of the Rubik's cube, if you solve the bottom two edges (including the centers), the rest of the cube will automatically solve itself. Sound familiar?

All you need to do is make sure the white center is on bottom (if it's not, you just need to do an `M2` to put white on bottom), then from there, do the swapping algorithm to put the **white** edges in their correct places - in other words, solve them into their position. Afterwards, the cube solves itself. Let's take a look at some examples:

<div id="end1">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`M' U2 M`)
    .alg(`M' U2 M`)
    ('#end1');
</script>
</div>

Here we just need to solve one of the white edges because the other one is already solved in place.

<div id="end2">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`M' U2 M'`)
    .alg(`M2 M U2 M'`)
    ('#end2');
</script>
</div>

Here `M2` first puts the white center on the bottom, then we can put the edges in their correct position.

<div id="end3">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`M2 U2 M' U2 M`)
    .alg(`M2 U2 M' U2 M`)
    ('#end3');
</script>
</div>

In this case, `M2` puts the white center on the bottom, and after that, on the `U` layer we only see one white edge (in this case the white-red edge), so when we want to solve it in place, we first need to move the edge to its position (which is in the axis where the white and red centers are), then swap the edges in question (which in this case is the front 2)

<div id="end4">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`M' U2 M2 U2 M'`)
    .alg(`M' U2 M M U2 M'`)
    ('#end4');
</script>
</div>

You can see here that the two white edges on the `U` layer are already directly above their solved position, so we just need to swap the front two edges, then swap the back two edges.

<div id="end5">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .case(`M2 U2 M2 U2`)
    .alg(`M' U2 M U2 M U2 M' U2 M' U2 M U2`)
    ('#end5');
</script>
</div>

The first `M' U2 M` brings one of the white edges to the `U` layer because we need to have one there to be able to execute swaps, then afterwards, we see that the edge that gets kicked out (the white-orange edge) needs to go to the back, so we can do `U2` to align the edge, then do a back swap (`M U2 M'`), then afterwards the white-red edge gets kicked out to the `U` layer, which from there, we can then align it with its position in the front with `U2`, then do a front swap (`M' U2 M`), then just do the last move to solve the rest of the cube.

> This case can actually be solved by doing `M2 U2 M2 U2` which directly solves both the white edges at the same time - but this isn't too important to learn for now.