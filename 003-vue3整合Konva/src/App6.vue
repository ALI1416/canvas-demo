<template>
  <div id="c" class="c"></div>
  <div id="c2" class="c"></div>
  <div id="c3" class="c"></div>
  <div id="c4" class="c"></div>
  <div id="c5" class="c"></div>
  <div id="c6" class="c"></div>
  <div id="c7" class="c"></div>
  <div id="c8" class="c"></div>
  <div id="c9" class="c"></div>
</template>

<script setup>
import Konva from "konva";
import {onMounted} from "vue"

onMounted(() => {
  /*  */
  const stage = new Konva.Stage({
    container: 'c',
    width: 300,
    height: 300
  });
  const layer = new Konva.Layer();
  stage.add(layer);
  /*  */
  const stage2 = new Konva.Stage({
    container: 'c2',
    width: 300,
    height: 300
  });
  const layer2 = new Konva.Layer();
  stage2.add(layer2);
  /*  */
  const stage3 = new Konva.Stage({
    container: 'c3',
    width: 300,
    height: 300
  });
  const layer3 = new Konva.Layer();
  stage3.add(layer3);
  /*  */
  const stage4 = new Konva.Stage({
    container: 'c4',
    width: 300,
    height: 300
  });
  const layer4 = new Konva.Layer();
  stage4.add(layer4);
  /*  */
  const stage5 = new Konva.Stage({
    container: 'c5',
    width: 300,
    height: 300
  });
  const layer5 = new Konva.Layer();
  stage5.add(layer5);
  /*  */
  const stage6 = new Konva.Stage({
    container: 'c6',
    width: 300,
    height: 300
  });
  const layer6 = new Konva.Layer();
  stage6.add(layer6);
  /*  */
  const stage7 = new Konva.Stage({
    container: 'c7',
    width: 300,
    height: 300
  });
  const layer7 = new Konva.Layer();
  stage7.add(layer7);
  /*  */
  const stage8 = new Konva.Stage({
    container: 'c8',
    width: 300,
    height: 300
  });
  const layer8 = new Konva.Layer();
  stage8.add(layer8);
  /*  */
  const stage9 = new Konva.Stage({
    container: 'c9',
    width: 300,
    height: 300
  });
  const layer9 = new Konva.Layer();
  stage9.add(layer9);
})
</script>
