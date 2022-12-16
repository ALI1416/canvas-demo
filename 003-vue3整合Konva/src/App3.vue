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
  <div id="c10" class="c"></div>
  <div id="c11" class="c"></div>
</template>

<script setup>
import Konva from "konva";
import {onMounted} from "vue"

onMounted(() => {
  /* 填充 */
  const stage = new Konva.Stage({
    container: 'c',
    width: 300,
    height: 300
  });
  const layer = new Konva.Layer();
  stage.add(layer);
  const rect = new Konva.Rect({
    x: 20,
    y: 20,
    width: 100,
    height: 100,
    // 颜色填充：默认无颜色
    fill: 'green',
    stroke: 'black',
  });
  layer.add(rect);
  const imageObj = new Image();
  imageObj.src = 'img/苹果.png';
  imageObj.onload = function () {
    const rect2 = new Konva.Rect({
      x: 150,
      y: 20,
      width: 100,
      height: 100,
      // 图片填充
      fillPatternImage: imageObj,
      // 图片填充偏移
      fillPatternOffset: {x: 20, y: 20},
      stroke: 'black',
    });
    layer.add(rect2);
  }
  const rect3 = new Konva.Rect({
    x: 20,
    y: 150,
    width: 100,
    height: 100,
    // 线性渐变起点
    fillLinearGradientStartPoint: {x: 0, y: 0},
    // 线性渐变终点
    fillLinearGradientEndPoint: {x: 100, y: 100},
    // 线性渐变比例和颜色
    fillLinearGradientColorStops: [0, 'red', 0.5, 'yellow', 1, 'blue'],
    stroke: 'black',
  });
  layer.add(rect3);
  const rect4 = new Konva.Rect({
    x: 150,
    y: 150,
    width: 100,
    height: 100,
    // 径向渐变起点
    fillRadialGradientStartPoint: {x: 50, y: 50},
    // 径向渐变起点半径
    fillRadialGradientStartRadius: 10,
    // 径向渐终点
    fillRadialGradientEndPoint: {x: 50, y: 50},
    // 径向渐变终点半径
    fillRadialGradientEndRadius: 50,
    // 径性渐变比例和颜色
    fillRadialGradientColorStops: [0, 'red', 0.5, 'yellow', 1, 'blue'],
    stroke: 'black',
  });
  layer.add(rect4);
  /* 轮廓 */
  const stage2 = new Konva.Stage({
    container: 'c2',
    width: 300,
    height: 300
  });
  const layer2 = new Konva.Layer();
  stage2.add(layer2);
  const rect5 = new Konva.Rect({
    x: 20,
    y: 20,
    width: 100,
    height: 100,
    fill: 'green',
    // 轮廓颜色：默认无轮廓
    stroke: 'black',
    // 轮廓宽度：默认1
    strokeWidth: 1
  });
  layer2.add(rect5);
  const rect6 = new Konva.Rect({
    x: 150,
    y: 20,
    width: 100,
    height: 100,
    fill: 'green',
    // 轮廓颜色
    stroke: 'blue',
    // 轮廓宽度
    strokeWidth: 10
  });
  layer2.add(rect6);
  /* 透明度 */
  const stage3 = new Konva.Stage({
    container: 'c3',
    width: 300,
    height: 300
  });
  const layer3 = new Konva.Layer();
  stage3.add(layer3);
  const rect7 = new Konva.Rect({
    x: 20,
    y: 20,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 1,
    // 透明度：默认1不透明
    opacity: 1
  });
  layer3.add(rect7);
  const rect8 = new Konva.Rect({
    x: 150,
    y: 20,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 1,
    opacity: 0.2
  });
  layer3.add(rect8);
  /* 阴影 */
  const stage4 = new Konva.Stage({
    container: 'c4',
    width: 300,
    height: 300
  });
  const layer4 = new Konva.Layer();
  stage4.add(layer4);
  const rect9 = new Konva.Rect({
    x: 20,
    y: 20,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 1,
    // 阴影颜色
    shadowColor: 'black',
    // 阴影模糊度
    shadowBlur: 10,
    // 阴影偏移
    shadowOffset: {x: 20, y: 10},
    // 阴影透明度
    shadowOpacity: 0.5
  });
  layer4.add(rect9);
  const text = new Konva.Text({
    text: 'Text Shadow!',
    fontFamily: 'Calibri',
    fontSize: 40,
    x: 20,
    y: 20,
    stroke: 'red',
    strokeWidth: 2,
    shadowColor: 'blue',
    shadowBlur: 0,
    shadowOffset: {x: 10, y: 10},
    shadowOpacity: 0.5
  });
  layer4.add(text);
  const line = new Konva.Line({
    stroke: 'black',
    strokeWidth: 10,
    lineJoin: 'round',
    lineCap: 'round',
    points: [50, 180, 250, 200],
    shadowColor: 'red',
    shadowBlur: 10,
    shadowOffset: {x: 10, y: 10},
    shadowOpacity: 0.8
  });
  layer4.add(line);
  /* 拐点 */
  const stage5 = new Konva.Stage({
    container: 'c5',
    width: 300,
    height: 300
  });
  const layer5 = new Konva.Layer();
  stage5.add(layer5);
  const rect10 = new Konva.Rect({
    x: 20,
    y: 20,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 20,
    // 默认：直角
    lineJoin: 'miter'
  });
  layer5.add(rect10);
  const rect11 = new Konva.Rect({
    x: 150,
    y: 20,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 20,
    // 平角
    lineJoin: 'bevel'
  });
  layer5.add(rect11);
  const rect12 = new Konva.Rect({
    x: 20,
    y: 150,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 20,
    // 圆角
    lineJoin: 'round'
  });
  layer5.add(rect12);
  /* 末端样式 */
  const stage6 = new Konva.Stage({
    container: 'c6',
    width: 300,
    height: 300
  });
  const layer6 = new Konva.Layer();
  stage6.add(layer6);
  const line2 = new Konva.Line({
    stroke: 'black',
    strokeWidth: 10,
    // 默认：直角
    lineCap: 'butt',
    points: [20, 50, 280, 50],
  });
  layer6.add(line2);
  const line3 = new Konva.Line({
    stroke: 'black',
    strokeWidth: 10,
    // 圆角
    lineCap: 'round',
    points: [20, 100, 280, 100],
  });
  layer6.add(line3);
  const line4 = new Konva.Line({
    stroke: 'black',
    strokeWidth: 10,
    // 方角
    lineCap: 'square',
    points: [20, 150, 280, 150],
  });
  layer6.add(line4);
  const line5 = new Konva.Line({
    stroke: 'red',
    points: [20, 10, 20, 290],
  });
  layer6.add(line5);
  const line6 = new Konva.Line({
    stroke: 'red',
    points: [280, 10, 280, 290],
  });
  layer6.add(line6);
  /* 虚线 */
  const stage7 = new Konva.Stage({
    container: 'c7',
    width: 300,
    height: 300
  });
  const layer7 = new Konva.Layer();
  stage7.add(layer7);
  const line7 = new Konva.Line({
    stroke: 'black',
    strokeWidth: 10,
    points: [20, 50, 280, 50],
    // 虚线
    dash: [20, 10]
  });
  layer7.add(line7);
  const line8 = new Konva.Line({
    stroke: 'black',
    strokeWidth: 10,
    points: [20, 100, 280, 100],
    // 虚线
    dash: [20, 10],
    // 虚线偏移：默认0
    dashOffset: -10
  });
  layer7.add(line8);
  /* 组合 */
  const stage8 = new Konva.Stage({
    container: 'c8',
    width: 300,
    height: 300
  });
  const layer8 = new Konva.Layer();
  stage8.add(layer8);
  const rect13 = new Konva.Rect({
    x: 20,
    y: 20,
    width: 100,
    height: 100,
    fill: 'green',
  });
  layer8.add(rect13);
  const rect14 = new Konva.Rect({
    x: 100,
    y: 100,
    width: 100,
    height: 100,
    fill: 'red',
    // 组合
    globalCompositeOperation: 'xor'
  });
  layer8.add(rect14);
  /* 显示和隐藏 */
  const stage9 = new Konva.Stage({
    container: 'c9',
    width: 300,
    height: 280
  });
  const layer9 = new Konva.Layer();
  stage9.add(layer9);
  const rect15 = new Konva.Rect({
    x: 20,
    y: 20,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    // 隐藏
    visible: false
  });
  layer9.add(rect15);
  const c9 = document.getElementById('c9').firstElementChild;
  c9.style.display = 'inline-block';
  const btn = document.createElement('button');
  c9.before(btn);
  btn.innerText = "显示";
  btn.addEventListener('click', function () {
    rect15.show();
  })
  const btn2 = document.createElement('button');
  c9.before(btn2);
  btn2.innerText = "隐藏";
  btn2.addEventListener('click', function () {
    rect15.hide();
  })
  /* 鼠标样式 */
  const stage10 = new Konva.Stage({
    container: 'c10',
    width: 300,
    height: 300
  });
  const layer10 = new Konva.Layer();
  stage10.add(layer10);
  const rect16 = new Konva.Rect({
    x: 20,
    y: 20,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 4,
    // 可拖拽
    draggable: true
  });
  layer10.add(rect16);
  rect16.on('mouseenter', function () {
    document.body.style.cursor = 'move';
  });
  rect16.on('mouseleave', function () {
    document.body.style.cursor = 'default';
  });
  /* 填充和轮廓绘制顺序 */
  const stage11 = new Konva.Stage({
    container: 'c11',
    width: 300,
    height: 300
  });
  const layer11 = new Konva.Layer();
  stage11.add(layer11);
  const text2 = new Konva.Text({
    text: 'false',
    x: 20,
    y: 20,
    fontSize: 50,
    stroke: 'green',
    fill: 'yellow',
    strokeWidth: 3,
  });
  layer11.add(text2);
  const text3 = new Konva.Text({
    text: 'true',
    x: 20,
    y: 120,
    fontSize: 50,
    stroke: 'green',
    fill: 'yellow',
    strokeWidth: 3,
    // 先轮廓后填充
    fillAfterStrokeEnabled: true,
  });
  layer11.add(text3);
})
</script>
