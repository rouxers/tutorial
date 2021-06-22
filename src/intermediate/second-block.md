<script type="text/javascript" src="/twistysim.js"></script>
<style type="text/css" rel="stylesheet">
/* modifies the opacity of the cube wireframe */
.ttk-shp-poly {
    stroke-opacity: 0.3;
}
</style>

# Second Block

## Objective

The goal of Second Block (SB) is to solve a `2x3x1` block on the right side of the cube (opposite to the first block you built).

<div id="inf1">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wtwwtwwtwggggggtttrtrrtrttttttttttttbbbbbbtttotootottt')
    ('#inf1');
</script>
</div>

## Basic Pair Insertions

While you can treat this step similarly to CFOP except using the M slice to orient edges as opposed to rotating, **this approach is fairly inefficient.**

When building SB, stick with a `<R, r, U, M>` moveset for now - there are places where doing F moves are useful, but as a beginner, avoiding using them completely for now will set somewhat decent fundamentals. Make sure to take SB slowly at the beginning and try to think of efficient solutions rather than blindly applying your knowledge from other methods.

Below are some inserts that are worth learning and setting up to when you see fit:

### Wide Insert

This insert is one of the most fundamental parts of Roux SB. 

<div id="inf2">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wtwwtwwtwggggggtttrtrrtrttttttttttttbbbbbbtttotootottt')
    .case(`r U r'`)
    ('#inf2');
</script>
</div>

There are quite a few cases where using the M slice to create this pair and insert this pair is going to be a good solution.

### Wide Insert (2)

<div id="inf3">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wtwwtwwtwggggggtttrtrrtrttttttttttttbbbbbbtttotootottt')
    .case(`r U' r'`)
    ('#inf3');
</script>
</div>

This case is less commonly seen compared to the other wide insert shown above, but it is still good to know about this solution. Some people may also see this as `M'` to pair the corner and the edge, and then `R U' R'` to insert, but the `M'` and the `R` at the beginning cancels, so you end up with a beginning `r` move instead.

> The two cases above can, and should, be mirrored to the back with `r' U' r` and `r' U r` respectively.

### Corner Solved

<div id="corner1">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wtwwtwwtwggggggtttrtrrtrttttttttttttbbbbbbtttotootottt')
    .case(`R U' M' U r'`)
    ('#corner1');
</script>
</div>

When you have a misoriented edge and a solved corner, you can use the `M` slice to pair up the corner and the edge as shown above.

### Corner Solved (2)

<div id="corner2">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wtwwtwwtwggggggtttrtrrtrttttttttttttbbbbbbtttotootottt')
    .case(`r U' M U R'`)
    ('#corner2');
</script>
</div>

When you have an oriented edge and a solved corner, you can use the `M` slice to pair up the corner and the edge as shown above.

### Regular Inserts

The normal CFOP style with moveset `<RU>` to insert pairs should also be used in Roux SB. If you ever need to use F moves (for example with `F' U' F`), you should instead use the M slice to orient the edge in question, then insert the pair using some form of `<RrU>`.

## Approach to Building a 2x2x1 Square

A `2x2x1` square is usually the first step of solving the second block, and can be built by either building the pair first, then doing some blockbuilding to solve the pair with the edge, or first solving the `DR` edge with some influencing, then solving any pair that comes afterwards.

Most top solvers solve the `DR` edge first mainly because it is easier to see FB + the `DR` edge in inspection. As a result, it is recommended that you use a `DR` first approach unless a pair presents itself for you after FB is built. 

## Applications

### Example 1

<div id="inf4">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wtwwtwwtwggggggtttrtrrtrttttttttttttbbbbbbtttotootottt')
    .case(`M U r U' r'`)
    ('#inf4');
</script>
</div>

While this pair is already solvable without rotating using CFOP, a *significantly* more efficient way of solving this pair would be to do an `M` move, then use one of the Roux-style wide inserts to solve the pair.

### Example 2

<div id="inf5">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wtwwtwwtwggggggtttrtrrtrttttttttttttbbbbbbtttotootottt')
    .case(`M R U' R'`)
    ('#inf5');
</script>
</div>

The solution to this (without rotating or using `F`/`B` moves) is fairly obvious, but it's worth mentioning just in case.

### Example 3

<div id="inf6">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wtwwtwwtwggggggtttrtrrtrttttttttttttbbbbbbtttotootottt')
    .case(`R U R' U r U' r'`)
    ('#inf6');
</script>
</div>

This case may be somewhat difficult to think of on the spot, but this case essentially is setting the corner up to an `r U' r'` insert.

### Example 4

<div id="ben">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wtwwtwwtwggggggtttrtrrtrttttttttttttbbbbbbtttotootottt')
    .case(`r U' r' U2 r U r'`)
    ('#ben');
</script>
</div>

This insert pairs up the corner and the edge with `r U' r'`, then the remaining portion is simply AUF into wide move insert.

## Other Resources to look at for further improvements:

Second Block is one of the hardest steps to get good at. It is highly recommended that you use the resources below to learn new approaches of solving SB rather than trying to learn everything by yourself.

- SBSquare (SS)
  - [F2B Tech: Build your SS Pair "Corner First"](https://www.youtube.com/watch?v=eGHJVvvbdXY)
  - [Zhouheng's SS Trainer](https://onionhoney.github.io/roux-trainers/#ss)
- SBPair (SP)
  - [Second Block Algs Document](https://docs.google.com/document/d/1bX50jAOM_veHsVJeLYGvSrH4uW9xrubep1zOSLdE4Vk/edit)
- General Resources:
  - [Zhouheng's FBDR Guide](https://raw.githubusercontent.com/Rouxles/roux-tutorial/master/fbdr/Zhouheng%27s%20FBDR%20Guide.pdf)
  - [Kavin Tangtartharakul's Example Solves](https://www.youtube.com/playlist?list=PLXiPs1z2Pwm5QPrtqB5J5rJ2DH6tbBU8T)
  - [Cubegrass SB, SS, SP Trainers](https://cubegrass.appspot.com/block_trainer/)

- [book.rouxers.com's FB page](https://book.rouxers.com/fb.html)