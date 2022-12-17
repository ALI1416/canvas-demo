<template>
  <div id="c" class="c"></div>
  <div id="c2" class="c"></div>
  <div id="c3" class="c"></div>
  <div id="c4" class="c"></div>
</template>

<script setup>
import Konva from "konva";
import {onMounted} from "vue"

onMounted(() => {
  /* 简单裁剪 */
  const stage = new Konva.Stage({
    container: 'c',
    width: 300,
    height: 300
  });
  const layer = new Konva.Layer();
  stage.add(layer);
  const group = new Konva.Group({
    // 创建裁剪区域
    clip: {
      x: 0,
      y: 0,
      width: 200,
      height: 200
    },
    draggable: true
  });
  layer.add(group);
  const circle = new Konva.Circle({
    x: 150,
    y: 150,
    radius: 100,
    fill: 'red'
  });
  group.add(circle);
  /* 复杂裁剪 */
  const stage2 = new Konva.Stage({
    container: 'c2',
    width: 300,
    height: 300
  });
  const layer2 = new Konva.Layer();
  stage2.add(layer2);
  const group2 = new Konva.Group({
    // 绘制裁剪区域
    clipFunc: function (ctx) {
      ctx.arc(150, 120, 60, 0, Math.PI * 2, false);
      ctx.arc(250, 120, 50, 0, Math.PI * 2, false);
    },
    draggable: true
  });
  layer2.add(group2);
  const circle2 = new Konva.Circle({
    x: 150,
    y: 150,
    radius: 100,
    fill: 'red'
  });
  group2.add(circle2);
  /* 组、层级 */
  const stage3 = new Konva.Stage({
    container: 'c3',
    width: 300,
    height: 280
  });
  const layer3 = new Konva.Layer();
  stage3.add(layer3);
  const group3 = new Konva.Group({
    x: 120,
    y: 20,
    rotation: 30
  });
  layer3.add(group3);
  const colors = ['red', 'orange', 'yellow', 'green', 'blue', 'purple'];
  let yellowBox;
  for (let i = 0; i < 6; i++) {
    let box = new Konva.Rect({
      x: i * 20,
      y: i * 10,
      width: 100,
      height: 50,
      name: colors[i],
      fill: colors[i],
      stroke: 'black',
      strokeWidth: 4,
      draggable: true,
    });
    if (colors[i] === 'yellow') {
      yellowBox = box;
    }
    group3.add(box);
  }
  const c3 = document.getElementById('c3').firstElementChild;
  c3.style.display = 'inline-block';
  const btn = document.createElement('button');
  c3.before(btn);
  btn.innerText = "置顶";
  btn.addEventListener('click', function () {
    yellowBox.moveToTop();
  });
  const btn2 = document.createElement('button');
  c3.before(btn2);
  btn2.innerText = "置底";
  btn2.addEventListener('click', function () {
    yellowBox.moveToBottom();
  });
  const btn3 = document.createElement('button');
  c3.before(btn3);
  btn3.innerText = "层级+1";
  btn3.addEventListener('click', function () {
    yellowBox.moveUp();
  });
  const btn4 = document.createElement('button');
  c3.before(btn4);
  btn4.innerText = "层级-1";
  btn4.addEventListener('click', function () {
    yellowBox.moveDown();
  });
  const btn5 = document.createElement('button');
  c3.before(btn5);
  btn5.innerText = "层级=2(恢复)";
  btn5.addEventListener('click', function () {
    yellowBox.zIndex(2);
  });
  /* 更换容器 */
  const stage4 = new Konva.Stage({
    container: 'c4',
    width: 300,
    height: 280
  });
  const layer4 = new Konva.Layer();
  stage4.add(layer4);
  const yellowGroup = new Konva.Group({
    x: 70,
    y: 70,
    draggable: true
  });
  const blueGroup = new Konva.Group({
    x: 150,
    y: 200,
    draggable: true
  });
  const rect = new Konva.Rect({
    x: 10,
    y: 10,
    width: 100,
    height: 50,
    fill: 'red',
    stroke: 'black'
  });
  const yellowCircle = new Konva.Circle({
    x: 0,
    y: 0,
    radius: 50,
    fill: 'yellow',
    stroke: 'black'
  });
  const blueCircle = new Konva.Circle({
    x: 0,
    y: 0,
    radius: 50,
    fill: 'blue',
    stroke: 'black'
  });
  yellowGroup.add(yellowCircle);
  yellowGroup.add(rect);
  blueGroup.add(blueCircle);
  layer4.add(yellowGroup);
  layer4.add(blueGroup);
  const c4 = document.getElementById('c4').firstElementChild;
  c4.style.display = 'inline-block';
  const btn6 = document.createElement('button');
  c4.before(btn6);
  btn6.innerText = "移到蓝色";
  btn6.addEventListener('click', function () {
    rect.moveTo(blueGroup);
  });
  const btn7 = document.createElement('button');
  c4.before(btn7);
  btn7.innerText = "移到黄色";
  btn7.addEventListener('click', function () {
    rect.moveTo(yellowGroup);
  });
})
</script>
