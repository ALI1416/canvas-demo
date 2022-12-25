<template>
  <div id="c" class="c"></div>
  <div id="c2" class="c" style="width: 420px;height: 420px"></div>
</template>

<script setup>
import Konva from "konva";
import {onMounted} from "vue"

onMounted(() => {
  /* 基本动画、控制器、事件、滤镜 */
  const stage = new Konva.Stage({
    container: 'c',
    width: 300,
    height: 280
  });
  const layer = new Konva.Layer();
  stage.add(layer);
  const text = new Konva.Text({
    x: 10,
    y: 10,
    fontFamily: 'Calibri',
    fontSize: 24,
    text: '',
    fill: 'black'
  });
  layer.add(text);
  const rect = new Konva.Rect({
    x: 20,
    y: 50,
    width: 100,
    height: 50,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 2,
    opacity: 0.5,
  });
  layer.add(rect);
  // 设置滤镜
  rect.cache();
  rect.filters([Konva.Filters.Noise]);
  rect.noise(0.5);
  // 定义动画结束状态
  const tween = new Konva.Tween({
    // 动画节点
    node: rect,
    // 持续时间(秒)
    duration: 5,
    // 动画效果
    easing: Konva.Easings.Linear,
    // 动画结束状态
    x: 180,
    y: 140,
    fill: 'red',
    rotation: Math.PI * 10,
    opacity: 1,
    strokeWidth: 6,
    scaleX: 1.2,
    scaleY: 1.2,
    // 完成事件
    onFinish: () => {
      text.text('动画完成');
    },
    // 滤镜
    noise: 1
  });
  const c = document.getElementById('c').firstElementChild;
  c.style.display = 'inline-block';
  const btn_play = document.createElement('button');
  c.before(btn_play);
  btn_play.innerText = "播放";
  btn_play.addEventListener('click', function () {
    // 播放
    tween.play();
  });
  const btn_pause = document.createElement('button');
  c.before(btn_pause);
  btn_pause.innerText = "暂停";
  btn_pause.addEventListener('click', function () {
    // 暂停
    tween.pause();
  });
  const btn_reverse = document.createElement('button');
  c.before(btn_reverse);
  btn_reverse.innerText = "倒回";
  btn_reverse.addEventListener('click', function () {
    // 倒回
    tween.reverse();
  });
  const btn_reset = document.createElement('button');
  c.before(btn_reset);
  btn_reset.innerText = "复原";
  btn_reset.addEventListener('click', function () {
    // 复原
    tween.reset();
  });
  const btn_finish = document.createElement('button');
  c.before(btn_finish);
  btn_finish.innerText = "结束";
  btn_finish.addEventListener('click', function () {
    // 结束
    tween.finish();
  });
  const btn_seek = document.createElement('button');
  c.before(btn_seek);
  btn_seek.innerText = "3秒";
  btn_seek.addEventListener('click', function () {
    // 到指定秒数位置
    tween.seek(3);
  });
  /* 动画效果 */
  const stage2 = new Konva.Stage({
    container: 'c2',
    width: 420,
    height: 400
  });
  const layer2 = new Konva.Layer();
  stage2.add(layer2);
  const tweens = [];
  const easings = [
    {name: '线性', value: 'Linear', color: 'blue'},
    {name: '缓入', value: 'EaseIn', color: 'green'},
    {name: '缓出', value: 'EaseOut', color: 'green'},
    {name: '缓入缓出', value: 'EaseInOut', color: 'green'},
    {name: '后退缓入', value: 'BackEaseIn', color: 'blue'},
    {name: '后退缓出', value: 'BackEaseOut', color: 'blue'},
    {name: '后退缓入缓出', value: 'BackEaseInOut', color: 'blue'},
    {name: '弹性缓入', value: 'ElasticEaseIn', color: 'green'},
    {name: '弹性缓出', value: 'ElasticEaseOut', color: 'green'},
    {name: '弹性缓入缓出', value: 'ElasticEaseInOut', color: 'green'},
    {name: '反弹缓入', value: 'BounceEaseIn', color: 'blue'},
    {name: '反弹缓出', value: 'BounceEaseOut', color: 'blue'},
    {name: '反弹缓入缓出', value: 'BounceEaseInOut', color: 'blue'},
    {name: '强缓入', value: 'StrongEaseIn', color: 'green'},
    {name: '强弹缓出', value: 'StrongEaseOut', color: 'green'},
    {name: '强缓入缓出', value: 'StrongEaseInOut', color: 'green'},
  ];
  for (let n = 0; n < easings.length; n++) {
    let num = n + 1;
    let ease = easings[n];
    let text2 = new Konva.Text({
      x: 10,
      y: (n * 400) / easings.length,
      padding: 4,
      text: num + ') ' + ease.name,
      fontSize: 18,
      fontFamily: 'Calibri',
      fill: ease.color,
    });
    layer2.add(text2);
    const tween2 = new Konva.Tween({
      node: text2,
      x: 280,
      easing: Konva.Easings[ease.value],
      duration: 2,
    });
    tweens.push(tween2);
  }
  const c2 = document.getElementById('c2').firstElementChild;
  c2.style.display = 'inline-block';
  const btn2_play = document.createElement('button');
  c2.before(btn2_play);
  btn2_play.innerText = "播放";
  btn2_play.addEventListener('click', function () {
    for (let t of tweens) {
      t.play();
    }
  });
  const btn2_pause = document.createElement('button');
  c2.before(btn2_pause);
  btn2_pause.innerText = "复原";
  btn2_pause.addEventListener('click', function () {
    for (let t of tweens) {
      t.reset();
    }
  });
})
</script>
