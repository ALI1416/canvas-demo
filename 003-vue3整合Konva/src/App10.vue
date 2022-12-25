<template>
  <div id="c" class="c"></div>
  <div id="c2" class="c"></div>
  <div id="c3" class="c"></div>
</template>

<script setup>
import Konva from "konva";
import {onMounted} from "vue"

onMounted(() => {
  /* 移动 */
  const stage = new Konva.Stage({
    container: 'c',
    width: 300,
    height: 280
  });
  const layer = new Konva.Layer();
  stage.add(layer);
  const rect = new Konva.Rect({
    x: 100,
    y: 100,
    width: 100,
    height: 60,
    fill: 'red'
  });
  layer.add(rect);
  const anim = new Konva.Animation(function (frame) {
    if (frame.time % 2000 < 1000) {
      // 改变位置
      rect.x(
          // frame.time 播放的总时间
          100 * Math.sin((frame.time * 2 * Math.PI) / 2000) + 100
      );
    } else {
      // 如需暂时动画，返回false
      return false;
    }
  }, layer);
  const c = document.getElementById('c').firstElementChild;
  c.style.display = 'inline-block';
  const btn_play = document.createElement('button');
  c.before(btn_play);
  btn_play.innerText = "开始";
  btn_play.addEventListener('click', function () {
    // 开始
    anim.start();
  });
  const btn_pause = document.createElement('button');
  c.before(btn_pause);
  btn_pause.innerText = "暂停";
  btn_pause.addEventListener('click', function () {
    // 暂停
    anim.stop();
  });
  /* 旋转 */
  const stage2 = new Konva.Stage({
    container: 'c2',
    width: 300,
    height: 280
  });
  const layer2 = new Konva.Layer();
  stage2.add(layer2);
  const rect2 = new Konva.Rect({
    x: 150,
    y: 130,
    width: 100,
    height: 60,
    fill: 'red',
    // 设置图形中心偏移
    offset: {
      x: 50,
      y: 30
    }
  });
  layer2.add(rect2);
  const anim2 = new Konva.Animation(function (frame) {
    // 按照图形中心旋转
    rect2.rotate((frame.timeDiff * 90) / 1000);
  }, layer2);
  const c2 = document.getElementById('c2').firstElementChild;
  c2.style.display = 'inline-block';
  const btn2_play = document.createElement('button');
  c2.before(btn2_play);
  btn2_play.innerText = "开始";
  btn2_play.addEventListener('click', function () {
    anim2.start();
  });
  const btn2_pause = document.createElement('button');
  c2.before(btn2_pause);
  btn2_pause.innerText = "暂停";
  btn2_pause.addEventListener('click', function () {
    anim2.stop();
  });
  /* 缩放 */
  const stage3 = new Konva.Stage({
    container: 'c3',
    width: 300,
    height: 280
  });
  const layer3 = new Konva.Layer();
  stage3.add(layer3);
  const rect3 = new Konva.Rect({
    x: 150,
    y: 130,
    width: 100,
    height: 60,
    fill: 'red',
    offset: {
      x: 50,
      y: 30
    }
  });
  layer3.add(rect3);
  const anim3 = new Konva.Animation(function (frame) {
    let scale = Math.sin((frame.time * 2 * Math.PI) / 2000) + 0.001;
    // 按照图形中心缩放
    rect3.scale({x: scale, y: scale});
  }, layer3);
  const c3 = document.getElementById('c3').firstElementChild;
  c3.style.display = 'inline-block';
  const btn3_play = document.createElement('button');
  c3.before(btn3_play);
  btn3_play.innerText = "开始";
  btn3_play.addEventListener('click', function () {
    anim3.start();
  });
  const btn3_pause = document.createElement('button');
  c3.before(btn3_pause);
  btn3_pause.innerText = "暂停";
  btn3_pause.addEventListener('click', function () {
    anim3.stop();
  });
})
</script>
