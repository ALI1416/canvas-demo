<template>
  <div id="c" class="c"></div>
  <div id="c2" class="c"></div>
  <div id="c3" class="c"></div>
  <div id="c4" class="c"></div>
  <div id="c5" class="c"></div>
  <div id="c6" class="c"></div>
  <div id="c7" class="c"></div>
  <div id="c8" class="c"></div>
</template>

<script setup>
import Konva from "konva";
import {onMounted} from "vue"

onMounted(() => {
  /* 拖拽 */
  const stage = new Konva.Stage({
    container: 'c',
    width: 300,
    height: 300
  });
  const layer = new Konva.Layer();
  stage.add(layer);
  const rect = new Konva.Rect({
    x: 100,
    y: 100,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 4,
    // 可拖拽
    draggable: true
  });
  layer.add(rect);
  rect.on('mouseenter', function () {
    document.body.style.cursor = 'move';
  });
  rect.on('mouseleave', function () {
    document.body.style.cursor = 'default';
  });
  /* 拖拽图片 */
  const stage2 = new Konva.Stage({
    container: 'c2',
    width: 300,
    height: 300
  });
  const layer2 = new Konva.Layer();
  stage2.add(layer2);
  Konva.Image.fromURL('img/橘子.png', function (tangerineImage) {
    tangerineImage.setAttrs({
      x: 100,
      y: 100,
      scaleX: 0.5,
      scaleY: 0.5,
      draggable: true
    });
    layer2.add(tangerineImage);
  });
  /* 拖拽组 */
  const stage3 = new Konva.Stage({
    container: 'c3',
    width: 300,
    height: 300
  });
  const layer3 = new Konva.Layer();
  stage3.add(layer3);
  const group = new Konva.Group({
    draggable: true
  });
  layer3.add(group);
  const colors = ['red', 'orange', 'yellow', 'green', 'blue', 'purple'];
  for (let i = 0; i < 6; i++) {
    let box = new Konva.Rect({
      x: i * 30 + 10,
      y: i * 20 + 40,
      width: 100,
      height: 50,
      name: colors[i],
      fill: colors[i],
      stroke: 'black',
      strokeWidth: 4
    });
    group.add(box);
  }
  /* 拖拽线条 */
  const stage4 = new Konva.Stage({
    container: 'c4',
    width: 300,
    height: 300
  });
  const layer4 = new Konva.Layer();
  stage4.add(layer4);
  const line = new Konva.Line({
    y: 50,
    points: [10, 70, 40, 23, 150, 60, 250, 20],
    stroke: 'blue',
    strokeWidth: 10,
    lineCap: 'round',
    lineJoin: 'round',
    dash: [29, 20, 0.001, 20],
    draggable: true
  });
  layer4.add(line);
  /* 拖动舞台 */
  const stage5 = new Konva.Stage({
    container: 'c5',
    width: 300,
    height: 300,
    // 空白区域可拖动
    draggable: true
  });
  const layer5 = new Konva.Layer();
  stage5.add(layer5);
  const circle = new Konva.Circle({
    x: stage.width() / 2,
    y: stage.height() / 2,
    radius: 70,
    fill: 'red',
    stroke: 'black',
    strokeWidth: 4
  });
  layer5.add(circle);
  /* 拖动事件 */
  const stage6 = new Konva.Stage({
    container: 'c6',
    width: 300,
    height: 300
  });
  const layer6 = new Konva.Layer();
  stage6.add(layer6);
  const text = new Konva.Text({
    x: 10,
    y: 10,
    fontFamily: 'Calibri',
    fontSize: 24,
    text: '',
    fill: 'black'
  });
  layer6.add(text);
  const rect2 = new Konva.Rect({
    x: 20,
    y: 50,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 4,
    draggable: true
  });
  layer6.add(rect2);
  rect2.on('dragstart', function () {
    text.text('开始');
  });
  rect2.on('dragend', function () {
    text.text('结束');
  });
  const circle2 = new Konva.Circle({
    x: 200,
    y: 200,
    radius: 70,
    fill: 'red',
    stroke: 'black',
    strokeWidth: 4,
    draggable: true
  });
  layer6.add(circle2);
  circle2.on('dragmove', function () {
    const pos = stage6.getPointerPosition();
    text.text('x: ' + pos.x + ', y: ' + pos.y);
  });
  /* 简单拖拽区域 */
  const stage7 = new Konva.Stage({
    container: 'c7',
    width: 300,
    height: 300
  });
  const layer7 = new Konva.Layer();
  stage7.add(layer7);
  const text2 = new Konva.Text({
    x: 20,
    y: 70,
    fontSize: 24,
    fontFamily: 'Calibri',
    text: '水平',
    fill: 'black',
    padding: 15,
    draggable: true,
    // 自定义拖拽边界(使用绝对坐标)
    dragBoundFunc: function (pos) {
      return {
        x: pos.x,
        y: this.absolutePosition().y
      };
    }
  });
  layer7.add(text2);
  const text3 = new Konva.Text({
    x: 150,
    y: 70,
    draggable: true,
    fontSize: 24,
    fontFamily: 'Calibri',
    text: '垂直',
    fill: 'black',
    padding: 15,
    dragBoundFunc: function (pos) {
      return {
        x: this.absolutePosition().x,
        y: pos.y
      };
    }
  });
  layer7.add(text3);
  /* 复杂拖拽区域 */
  const stage8 = new Konva.Stage({
    container: 'c8',
    width: 300,
    height: 300
  });
  const layer8 = new Konva.Layer();
  stage8.add(layer8);
  const rect3 = new Konva.Rect({
    x: 100,
    y: 100,
    width: 50,
    height: 50,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 4,
    draggable: true,
    // 限制在正方形区域内拖动
    dragBoundFunc: function (pos) {
      return {
        x: pos.x < 50 ? 50 : (pos.x > 200 ? 200 : pos.x),
        y: pos.y < 50 ? 50 : (pos.y > 200 ? 200 : pos.y)
      };
    }
  });
  layer8.add(rect3);
  const circle3 = new Konva.Circle({
    x: 200,
    y: 200,
    radius: 25,
    fill: 'red',
    stroke: 'black',
    strokeWidth: 4,
    draggable: true,
    // 限制在圆形区域内拖动
    dragBoundFunc: function (pos) {
      let cx = 150;
      let cy = 150;
      let r = 100;
      let dx = pos.x - cx;
      let dy = pos.y - cy;
      let scale = r / Math.sqrt(dx * dx + dy * dy);
      if (scale > 1) {
        return pos;
      } else {
        return {
          x: dx * scale + cx,
          y: dy * scale + cy
        }
      }
    }
  });
  layer8.add(circle3);
})
</script>
