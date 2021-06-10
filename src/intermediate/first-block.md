<script type="text/javascript" src="/twistysim.js"></script>
<style type="text/css" rel="stylesheet">
/* modifies the opacity of the cube wireframe */
.ttk-shp-poly {
    stroke-opacity: 0.3;
}
</style>

# First Block

## Objective

The goal of First Block (FB) is to solve a `2x3x1` block on the left side of the cube.

Below is a visual cube showing what an FB looks like that you can move around - try it yourself!

<div id="inf1">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wttwttwtttttttttttrttrttttttttttttttbbbbbbtttttottottt')
    ('#inf1');
</script>

This tutorial will use the same orientation for all first blocks, but to make the most of each scramble, be able to solve with yellow/white on bottom with any color on the side at the minimum (x2 y color neutrality). If you come from a CN CFOP background, it might be worth it to go for full CN right from the beginning.

This step should be fairly simple if you have a background in cubing, but it is still highly recommended that you read the examples below.

## Approaches to solving FB

### DL First

One fairly simple approach is to solve the DL piece first (like you would in the cross), then solve the other 2 pairs individually. This approach is quite useful but don't rely on it to give you the best solutions all the time.

**Example 1:**

<div id="inf2">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wttwttwtttttttttttrttrttttttttttttttbbbbbbtttttottottt')
    .case(`D U R U' R U2 F' U R U2 B`)
    ('#inf2');
</script>

This approach is very rudimentary but can get you going (for now).

`D` solves DL into its place, then `U R U' R` pairs up the blue-red-white pair in a CFOP-like manner, which can then be inserted into its slot with `U2 F'`. Next, the other pair can be paired up in 2 moves (`U R`) which then can be solved either by doing `U2 B` like shown in the visual cube, or `r2 B'`. Both these approaches for inserting pairs are very useful to get used to - try to break CFOP habits for FB when it comes to inserting pairs into their respective slots.

</div>

**Example 2:**

<div id="inf3">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wttwttwtttttttttttrttrttttttttttttttbbbbbbtttttottottt')
    .case(`D M' U2 B U2 r' U' R' F`)
    ('#inf3');
</script>

This approach is very rudimentary but can get you going (for now).

`D` solves DL into its place, `M'` pairs the blue-orange-white pair up, which is then inserted using `U2 B`, which sets up the next pair to be solved with `U2 r' U'` to insert the edge to DF, then the corner can be paired up with `R'`, which can then be solved into its slot with `F`.

</div>

### Line-Line 2x2x1 + Pair

**Example 2:**

<div id="inf4">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wttwttwtttttttttttrttrttttttttttttttbbbbbbtttttottottt')
    .case(`R' U' R' u U R' U2 B`)
    ('#inf4');
</script>

For this example, the line-line already given by the scramble is the blue-red-white pair with two white pieces on bottom. This means that to get to a `2x2x1` square, all that needs to be done is to solve the blue center and the blue-red edge, which can be done either by doing some form of a `D` move or some form of a `u` move (which is used in the example shown above). The initial `R'` is done to setup the next pair - if you can't see this in inspection yet, you don't need to worry about it for now - then `U' R'` solves the square by pairing the center with the edge, then doing a `u` move solves a 2x2x1 square. Afterwards, the other pair is solved. (This pair could also be done with `U M' r B'`)

</div>

<div id="inf5">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wttwttwtttttttttttrttrttttttttttttttbbbbbbtttttottottt')
    .case(`r' U' R2 D' U B`)
    ('#inf5');
</script>

In this example, we have a center + edge solved, so we just need to solve the edge and corner corresponding to those pieces to solve the `2x2x1` square, then solve the pair afterwards. The line can be solved by doing `r' U' R2` which can then be solved into position with a `D'` move, then the remaining pair can be solved by doing `U B`.

</div>

### S Move Insert

**Example 2:**

<div id="inf6">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wttwttwtttttttttttrttrttttttttttttttbbbbbbtttttottottt')
    .case(`M' U M' S' U' R' U2 F'`)
    ('#inf6');
</script>

Usually an S move (or f move) insert can be done if there is a pair already solved. You can first position the cube where the pair is already solved (either at the back or at the front FB slot), then solve the DL edge and the center, then solve it into place with an S move of some sort. You can also **solve the two pairs first, then insert the center and the edge last** if it leads to a better solution.

In the example above, `M' U M'` is done to set up the edge and the center in a position where `S'` can insert it, then the last pair can be solved by doing `U' R' U2 F'`.

</div>

### Line-Line

**Example 2:**

<div id="inf7">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wttwttwtttttttttttrttrttttttttttttttbbbbbbtttttottottt')
    .case(`u2 F2 R' U' R D`)
    ('#inf7');
</script>

The line-line approach is sometimes really useful, but forcing it usually doesn't yield great results. 

For this case, `u2 F2` solves the edge `1x1x3` line, then `R' U' R` solves the corner `1x1x3` line, which can then be solved with a `D` move.
</div>

## Other Resources to look at for improvement:

- [book.rouxers.com's FB page](https://book.rouxers.com/fb.html)