<script type="text/javascript" src="/twistysim.js"></script>
<style type="text/css" rel="stylesheet">
/* modifies the opacity of the cube wireframe */
.ttk-shp-poly {
    stroke-opacity: 0.3;
}
</style>

# Move Notation

> TL;DR: [Look at this link for a .gif on all the possible cube moves.](https://assets1.ello.co/uploads/asset/attachment/4123434/ello-optimized-81fbd399.gif).
> 
> If you ever need any visual cube representation of what would happen to the cube when you input typed moves, use [cubedb.net](https://cubedb.net/)

## Basic Moves

If you hold the cube in a fixed position, there are 6 sides of the cubes that can be turned, which are the following:

1. Top/Up (`U`)
2. Left (`L`)
3. Front (`F`)
4. Right (`R`)
5. Back (`B`)
6. Bottom/Down (`D`)

In addition, there are 3 different types of arguments that can be applied to the end of each move to change how that move is executed:

1. Single Letter (Turn clockwise)
2. Single Letter + `'` (Turn face anticlockwise)
3. Single Letter + `2` (Do a double turn on that face)

> Some of the direction of the moves might be counter-intuitive in the beginning, for example `D` and `B` moves. The way to see which direction these moves go in is to have the `D` or `B` side face you, then turn that face either clockwise or anticlockwise depending on the argument provided.

A good way to familiarize yourself with the notation is to see it in action. Below you can see a few examples of what the notation looks like! (Pay attention to the direction that the moves go in, and also try executing them on your own cube)

### U moves

<div id="U">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .movePeriod(1000)
    .alg(`U U' U2`)
    ('#U');
</script>

### L moves

<div id="L">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .movePeriod(1000)
    .alg(`L L' L2`)
    ('#L');
</script>

### F moves

<div id="F">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .movePeriod(1000)
    .alg(`F F' F2`)
    ('#F');
</script>

### R moves

<div id="R">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .movePeriod(1000)
    .alg(`R R' R2`)
    ('#R');
</script>

### B moves

<div id="B">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .movePeriod(1000)
    .alg(`B B' B2`)
    ('#B');
</script>

### D moves

<div id="D">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .movePeriod(1000)
    .alg(`D D' D2`)
    ('#D');
</script>

## Rotations

There also is notation to rotate the **whole** cube along the `x`, `y`, and `z` axes.

You could imagine rotating the cube around those axes, but a potentially easier way to remember the direction of the rotations is to realize that `x`, `y`, and `z` follow the direction of `R`, `U`, and `F` respectively. You could imagine an `x'` rotation like doing an `R'` move, but on **all** the layers rather than just the outer layer. If you're still confused, look at the visual representations:

### x rotations

<div id="x">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .movePeriod(1000)
    .alg(`x x' x2`)
    ('#x');
</script>

### y rotations

<div id="y">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .movePeriod(1000)
    .alg(`y y' y2`)
    ('#y');
</script>

### z rotations

<div id="z">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .movePeriod(1000)
    .alg(`z z' z2`)
    ('#z');
</script>

## Moves useful for the Roux Method

There are some additional pieces of notation that can be derived by using a combination of a *move* and a *rotation*, but in the context of Roux solving, it is far easier to deal with it by learning new notation that covers those specific moves. 

These moves are the middle slice move `M`, and the wide R move `Rw` or `r`. While there are some other versions of these moves, you only really need to know the moves mentioned above for the Roux method. A visual representation of the moves can be seen below:

### M slice moves

Notice that the direction is somewhat counter-intuitive! `M` follows the direction of `L` moves rather than `R` moves, so take some time to get used to that.

It is worth noting that knowing the direction of `M` will not be necessary to solve the cube due to the intuitive nature of Roux (the visuals should be good enough), but it may help in the future.

<div id="M">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .movePeriod(1000)
    .alg(`M M' M2`)
    ('#M');
</script>

### Wide R moves

`Rw` and `r` are functionally the exact same on a 3x3. `r` is shorter, so this tutorial will use `r` throughout, but if you see `Rw` somewhere else on a 3x3 related tutorial, know that they are the same thing.

<div id="Rw">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wwwwwwwwwgggggggggrrrrrrrrryyyyyyyyybbbbbbbbbooooooooo')
    .movePeriod(1000)
    .alg(`r r' r2`)
    ('#Rw');
</script>

> The `w` in `Rw` stands for 'wide'