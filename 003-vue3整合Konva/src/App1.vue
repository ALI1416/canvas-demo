<template>
  <!-- div中放入canvas -->
  <div id="c" class="c"></div>
</template>

<script setup>
/* 0、安装并导入依赖 */
// 安装 npm install konva
import Konva from "konva";
import {onMounted} from "vue"

onMounted(() => {
  /* Konva */
  // Stage(舞台)  一个canvas对应一个stage
  // Layer(图层)  stage下可以有多个layer
  // Group(组)   layer和group下可以有多个group
  // Shape(图形)  layer和group下可以有多个shape

  /* 1、创建一个舞台 */
  const stage = new Konva.Stage({
    // 指定canvas的容器，默认是id，`#`开头是id，`.`开头是class
    container: 'c',
    // canvas宽
    width: 300,
    // canvas高
    height: 300
  });
  /* 2、创建图层 */
  const layer = new Konva.Layer();
  /* 3、创建图形(圆) */
  const circle = new Konva.Circle({
    // 圆的x
    x: stage.width() / 2,
    // 圆的y
    y: stage.height() / 2,
    // 半径
    radius: 70,
    // 填充颜色
    fill: 'red',
    // 轮廓颜色
    stroke: 'black',
    // 轮廓宽度
    strokeWidth: 4
  });
  /* 4、图形添加进图层 */
  layer.add(circle);
  /* 5、图层添加进舞台 */
  stage.add(layer);
})
</script>
