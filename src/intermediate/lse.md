<script type="text/javascript" src="/twistysim.js"></script>
<style type="text/css" rel="stylesheet">
/* modifies the opacity of the cube wireframe */
.ttk-shp-poly {
    stroke-opacity: 0.3;
}
</style>

# LSE

## Objective

## Edge Orientation (EO)

The first 'step' of LSE is to orient all the edges. This means that assuming you solve your blocks with white or yellow on the `D` layer, you would want all the white/yellow facelets to be on the `U` or `D` face as shown by the purple facelets in the visual below.

<div id="inf1">
<script type="text/javascript">
  TTk.AlgorithmPuzzle(3)
    .size({width:300, height:300})
    .fc('wmwwtwwmwggggggglgrlrrtrrlrymymmmymybbbbbbblbolootoolo')
    ('#inf1');
</script>
</div>

This step can be done by setting up to an *arrow* case.