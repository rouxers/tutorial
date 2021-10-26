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

This tutorial will use the **same orientation for all first blocks**. This means that for every example, the Blue-White first block will be the one to solve (check the visual if you aren't sure what that means)

## Steps to Solving FB

### Orient your Centers

In this step, all you need to do is rotate the cube such that the blue center is on the left, and the green center is on the right.

After you do this, you should not change the position of the left and right centers throughout the whole solve — they should be fixed with blue on left and green on right even up until the cube is fully solved.

Your cube's centers should look like that in the visual below.

<div id="centers">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('tttttttttttttgttttttttttttttttttttttttttbttttttttttttt')
    ('#centers');
</script>

> Notice that you only need to look at the green and blue centers! No other center colours matter until the last step.

### Solve the White-Blue edge piece

The first step is to solve the white-blue edge piece relative to its center. Once you're done, the white facelet should be facing downwards.

Note that the blue facelet on the blue-white edge should match with the blue center — not the other way around.

Below, you will see a few examples of how to insert the blue-white edge in place.

#### Example: 1 move away

<div id="DL">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('tttwtttttttttgtttttttttttttttttttttttbttbttttttttttttt')
    .case('D2')
    ('#DL');
</script>

#### Example: L2 away

<div id="DL-L2">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('tttwtttttttttgtttttttttttttttttttttttbttbttttttttttttt')
    .case('L2')
    ('#DL-L2');
</script>

#### Example: Weird position

<div id="DL-weird">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('tttwtttttttttgtttttttttttttttttttttttbttbttttttttttttt')
    .case(`B' D`)
    ('#DL-weird');
</script>

#### Example: Edge flipped in place

<div id="DLflip">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('tttwtttttttttgtttttttttttttttttttttttbttbttttttttttttt')
    .case('D F L')
    ('#DLflip');
</script>

`or`

<div id="DLflip2">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('tttwtttttttttgtttttttttttttttttttttttbttbttttttttttttt')
    .case(`L2 U' r' D'`)
    ('#DLflip2');
</script>

(There are many possibilities — just experiment and see what works.)

### Building the First Block Square (2x1x1)

Once you're done with that, you're ready to move onto solving a `2x1x1` using either the Blue-Red-White or Blue-Orange-White pairs.

To do that, we first need to know what a `pair` is.

#### What is a pair?

