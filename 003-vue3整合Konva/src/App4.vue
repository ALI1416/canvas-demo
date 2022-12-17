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
  <div id="c12" class="c"></div>
  <div id="c13" class="c"></div>
  <div id="c14" class="c"></div>
  <div id="c15" class="c"></div>
</template>

<script setup>
import Konva from "konva";
import {onMounted} from "vue"

onMounted(() => {
  /* 鼠标事件绑定 */
  const stage = new Konva.Stage({
    container: 'c',
    width: 300,
    height: 300
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
  const triangle = new Konva.RegularPolygon({
    x: 80,
    y: 120,
    sides: 3,
    radius: 80,
    fill: '#00D2FF',
    stroke: 'black',
    strokeWidth: 4
  });
  layer.add(triangle);
  triangle.on('mousemove', function () {
    const pos = stage.getPointerPosition();
    text.text('x: ' + pos.x + ', y: ' + pos.y);
  });
  const circle = new Konva.Circle({
    x: 230,
    y: 100,
    radius: 60,
    fill: 'red',
    stroke: 'black',
    strokeWidth: 4
  });
  layer.add(circle);
  circle.on('mouseover', function () {
    text.text('进入');
  });
  circle.on('mouseout', function () {
    text.text('离开');
  });
  circle.on('mousedown', function () {
    text.text('按下');
  });
  circle.on('mouseup', function () {
    text.text('抬起');
  });
  const rect = new Konva.Rect({
    x: 20,
    y: 180,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 4
  });
  layer.add(rect);
  rect.on('click', function () {
    text.text('单击');
  });
  rect.on('dblclick', function () {
    text.text('双击');
  });
  /* 图片事件 */
  const stage2 = new Konva.Stage({
    container: 'c2',
    width: 300,
    height: 300
  });
  const layer2 = new Konva.Layer();
  stage2.add(layer2);
  const text2 = new Konva.Text({
    x: 10,
    y: 10,
    fontFamily: 'Calibri',
    fontSize: 24,
    text: '',
    fill: 'black'
  });
  layer2.add(text2);
  Konva.Image.fromURL('img/狮子.png', function (lionImage) {
    lionImage.setAttrs({
      x: 20,
      y: 20,
    });
    layer2.add(lionImage);
    lionImage.on('mouseover', function () {
      text2.text('进入');
    });
    lionImage.on('mouseout', function () {
      text2.text('离开');
    });
  });
  Konva.Image.fromURL('img/狮子.png', function (lionImage) {
    lionImage.setAttrs({
      x: 150,
      y: 150,
    });
    layer2.add(lionImage);
    // 缓存图片
    lionImage.cache();
    // 忽略透明像素
    lionImage.drawHitFromCache();
    lionImage.on('mouseover', function () {
      text2.text('进入');
    });
    lionImage.on('mouseout', function () {
      text2.text('离开');
    });
  });
  /* 移动端触摸事件 */
  const stage3 = new Konva.Stage({
    container: 'c3',
    width: 300,
    height: 300
  });
  const layer3 = new Konva.Layer();
  stage3.add(layer3);
  const text3 = new Konva.Text({
    x: 10,
    y: 10,
    fontFamily: 'Calibri',
    fontSize: 24,
    text: '',
    fill: 'black'
  });
  layer3.add(text3);
  const triangle2 = new Konva.RegularPolygon({
    x: 80,
    y: 120,
    sides: 3,
    radius: 80,
    fill: '#00D2FF',
    stroke: 'black',
    strokeWidth: 4
  });
  layer3.add(triangle2);
  triangle2.on('touchmove', function () {
    const pos = stage3.getPointerPosition();
    text3.text('x: ' + pos.x + ', y: ' + pos.y);
  });
  const circle2 = new Konva.Circle({
    x: 230,
    y: 100,
    radius: 60,
    fill: 'red',
    stroke: 'black',
    strokeWidth: 4
  });
  layer3.add(circle2);
  circle2.on('touchstart', function () {
    text3.text('按下');
  });
  circle2.on('touchmove', function () {
    text3.text('移动');
  });
  circle2.on('touchend', function () {
    text3.text('抬起');
  });
  const rect2 = new Konva.Rect({
    x: 20,
    y: 180,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 4
  });
  layer3.add(rect2);
  rect2.on('tap', function () {
    text3.text('单击');
  });
  rect2.on('dbltap', function () {
    text3.text('双击');
  });
  /* 移动端滚动事件 */
  const stage4 = new Konva.Stage({
    container: 'c4',
    width: 300,
    height: 300
  });
  const layer4 = new Konva.Layer();
  stage4.add(layer4);
  // 拖动绿色不会滚动页面
  const rect3 = new Konva.Rect({
    x: 20,
    y: 20,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 4
  });
  layer4.add(rect3);
  // 拖动红色会滚动页面
  const rect4 = new Konva.Rect({
    x: 150,
    y: 150,
    width: 100,
    height: 100,
    fill: 'red',
    stroke: 'black',
    strokeWidth: 4,
    // 阻止默认事件：允许滚动事件：默认不允许
    preventDefault: false
  });
  layer4.add(rect4);
  /* 多重事件 */
  const stage5 = new Konva.Stage({
    container: 'c5',
    width: 300,
    height: 300
  });
  const layer5 = new Konva.Layer();
  stage5.add(layer5);
  const text4 = new Konva.Text({
    x: 10,
    y: 10,
    fontFamily: 'Calibri',
    fontSize: 24,
    text: '',
    fill: 'black'
  });
  layer5.add(text4);
  const rect5 = new Konva.Rect({
    x: 50,
    y: 50,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 4
  });
  layer5.add(rect5);
  let count = 0;
  rect5.on('mouseover mouseout mousedown mouseup', function () {
    text4.text('事件计数：' + ++count);
  });
  /* 桌面端和移动端组合事件 */
  const stage6 = new Konva.Stage({
    container: 'c6',
    width: 300,
    height: 300
  });
  const layer6 = new Konva.Layer();
  stage6.add(layer6);
  const text5 = new Konva.Text({
    x: 10,
    y: 10,
    fontFamily: 'Calibri',
    fontSize: 24,
    text: '',
    fill: 'black'
  });
  layer6.add(text5);
  const triangle3 = new Konva.RegularPolygon({
    x: 80,
    y: 120,
    sides: 3,
    radius: 80,
    fill: '#00D2FF',
    stroke: 'black',
    strokeWidth: 4
  });
  layer6.add(triangle3);
  triangle3.on('mousemove touchmove', function () {
    const pos = stage6.getPointerPosition();
    text5.text('x: ' + pos.x + ', y: ' + pos.y);
  });
  const circle3 = new Konva.Circle({
    x: 230,
    y: 100,
    radius: 60,
    fill: 'red',
    stroke: 'black',
    strokeWidth: 4
  });
  layer6.add(circle3);
  circle3.on('mousedown touchstart', function () {
    text5.text('按下');
  });
  circle3.on('mouseup touchend', function () {
    text5.text('抬起');
  });
  const rect6 = new Konva.Rect({
    x: 20,
    y: 180,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 4
  });
  layer6.add(rect6);
  rect6.on('click tap', function () {
    text5.text('单击');
  });
  rect6.on('dblclick dbltap', function () {
    text5.text('双击');
  });
  /* 自定义事件监听范围 */
  const stage7 = new Konva.Stage({
    container: 'c7',
    width: 300,
    height: 280
  });
  const layer7 = new Konva.Layer();
  stage7.add(layer7);
  const text6 = new Konva.Text({
    x: 10,
    y: 10,
    fontFamily: 'Calibri',
    fontSize: 24,
    text: '',
    fill: 'black'
  });
  layer7.add(text6);
  const triangle4 = new Konva.RegularPolygon({
    x: 80,
    y: 120,
    sides: 3,
    radius: 80,
    fill: '#00D2FF',
    stroke: 'black',
    strokeWidth: 4,
    // 自定义事件监听范围
    hitFunc: function (context) {
      context.beginPath();
      context.rect(-20, -20, 40, 40);
      context.closePath();
      context.fillStrokeShape(this);
    }
  });
  layer7.add(triangle4);
  triangle4.on('mousemove', function () {
    const pos = stage7.getPointerPosition();
    text6.text('x: ' + pos.x + ', y: ' + pos.y);
  });
  const line = new Konva.Line({
    x: 50,
    y: 100,
    points: [100, 100, 150, 100, 150, 150, 100, 150],
    tension: 1,
    strokeWidth: 1,
    stroke: 'black',
    // 自定义事件监听范围的宽度
    hitStrokeWidth: 20
  });
  layer7.add(line);
  line.on('mousemove', function () {
    const pos = stage7.getPointerPosition();
    text6.text('x: ' + pos.x + ', y: ' + pos.y);
  });
  const c7 = document.getElementById('c7').firstElementChild;
  c7.style.display = 'inline-block';
  const btn = document.createElement('button');
  c7.before(btn);
  btn.innerText = "显示/隐藏自定义事件监听范围";
  btn.addEventListener('click', function () {
    // 显示/隐藏自定义事件监听范围
    layer7.toggleHitCanvas();
  })
  /* 移除事件监听 */
  const stage8 = new Konva.Stage({
    container: 'c8',
    width: 300,
    height: 280
  });
  const layer8 = new Konva.Layer();
  stage8.add(layer8);
  const text7 = new Konva.Text({
    x: 10,
    y: 10,
    fontFamily: 'Calibri',
    fontSize: 24,
    text: '',
    fill: 'black'
  });
  layer8.add(text7);
  const rect7 = new Konva.Rect({
    x: 50,
    y: 50,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 4
  });
  layer8.add(rect7);
  rect7.on('mouseover', function () {
    text7.text('进入');
  });
  const rect8 = new Konva.Rect({
    x: 170,
    y: 170,
    width: 100,
    height: 100,
    fill: 'red',
    stroke: 'black',
    strokeWidth: 4
  });
  layer8.add(rect8);
  rect8.on('mouseout.e1', function () {
    text7.text('离开1');
  });
  rect8.on('mouseout.e2', function () {
    alert('离开2');
  });
  const c8 = document.getElementById('c8').firstElementChild;
  c8.style.display = 'inline-block';
  const btn2 = document.createElement('button');
  c8.before(btn2);
  btn2.innerText = "移除进入";
  btn2.addEventListener('click', function () {
    // 通过事件移除
    rect7.off('mouseover');
    text7.text('移除进入');
  })
  const btn3 = document.createElement('button');
  c8.before(btn3);
  btn3.innerText = "移除离开1";
  btn3.addEventListener('click', function () {
    // 通过事件名称移除
    rect8.off('mouseout.e1');
    text7.text('移除离开1');
  })
  const btn4 = document.createElement('button');
  c8.before(btn4);
  btn4.innerText = "移除离开2";
  btn4.addEventListener('click', function () {
    rect8.off('mouseout.e2');
    text7.text('移除离开2');
  })
  const btn5 = document.createElement('button');
  c8.before(btn5);
  btn5.innerText = "移除离开";
  btn5.addEventListener('click', function () {
    rect8.off('mouseout');
    text7.text('移除离开');
  })
  /* 是否监听 */
  const stage9 = new Konva.Stage({
    container: 'c9',
    width: 300,
    height: 280
  });
  const layer9 = new Konva.Layer();
  stage9.add(layer9);
  const text8 = new Konva.Text({
    x: 10,
    y: 10,
    fontFamily: 'Calibri',
    fontSize: 24,
    text: '',
    fill: 'black'
  });
  layer9.add(text8);
  const rect9 = new Konva.Rect({
    x: 50,
    y: 50,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 4,
    // 关闭监听
    listening: false
  });
  layer9.add(rect9);
  rect9.on('mousemove', function () {
    const pos = stage9.getPointerPosition();
    text8.text('x: ' + pos.x + ', y: ' + pos.y);
  });
  const c9 = document.getElementById('c9').firstElementChild;
  c9.style.display = 'inline-block';
  const btn6 = document.createElement('button');
  c9.before(btn6);
  btn6.innerText = "打开监听";
  btn6.addEventListener('click', function () {
    rect9.listening(true);
    text8.text('打开监听');
  })
  const btn7 = document.createElement('button');
  c9.before(btn7);
  btn7.innerText = "关闭监听";
  btn7.addEventListener('click', function () {
    rect9.listening(false);
    text8.text('关闭监听');
  })
  /* 冒泡事件 */
  const stage10 = new Konva.Stage({
    container: 'c10',
    width: 300,
    height: 300
  });
  const layer10 = new Konva.Layer();
  layer10.on('click', function () {
    alert('layer10')
  });
  stage10.add(layer10);
  const rect10 = new Konva.Rect({
    x: 20,
    y: 20,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 4
  });
  layer10.add(rect10);
  rect10.on('click', function (event) {
    // 阻止冒泡事件
    event.cancelBubble = true;
    alert('rect10')
  });
  const rect11 = new Konva.Rect({
    x: 150,
    y: 150,
    width: 100,
    height: 100,
    fill: 'red',
    stroke: 'black',
    strokeWidth: 4
  });
  layer10.add(rect11);
  rect11.on('click', function () {
    alert('rect11')
  });
  /* 事件委托 */
  const stage11 = new Konva.Stage({
    container: 'c11',
    width: 300,
    height: 300
  });
  const layer11 = new Konva.Layer();
  stage11.add(layer11);
  const text9 = new Konva.Text({
    x: 10,
    y: 10,
    fontFamily: 'Calibri',
    fontSize: 24,
    text: '',
    fill: 'black'
  });
  layer11.add(text9);
  layer11.on('click', function (event) {
    // 通过event.target获取上级对象
    text9.text(event.target.fill());
  });
  const rect12 = new Konva.Rect({
    x: 50,
    y: 50,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 4
  });
  layer11.add(rect12);
  const rect13 = new Konva.Rect({
    x: 170,
    y: 170,
    width: 100,
    height: 100,
    fill: 'red',
    stroke: 'black',
    strokeWidth: 4
  });
  layer11.add(rect13);
  /* 事件触发 */
  const stage12 = new Konva.Stage({
    container: 'c12',
    width: 300,
    height: 280
  });
  const layer12 = new Konva.Layer();
  stage12.add(layer12);
  const text10 = new Konva.Text({
    x: 10,
    y: 10,
    fontFamily: 'Calibri',
    fontSize: 24,
    text: '',
    fill: 'black'
  });
  layer12.add(text10);
  const rect14 = new Konva.Rect({
    x: 50,
    y: 50,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 4
  });
  layer12.add(rect14);
  rect14.on('click', function () {
    text10.text('点击');
  });
  rect14.on('mouseout', function () {
    text10.text('离开');
  });
  const c12 = document.getElementById('c12').firstElementChild;
  c12.style.display = 'inline-block';
  const btn8 = document.createElement('button');
  c12.before(btn8);
  btn8.innerText = "手动触发点击事件";
  btn8.addEventListener('click', function () {
    rect14.fire('click');
  })
  /* 舞台事件 */
  const stage13 = new Konva.Stage({
    container: 'c13',
    width: 300,
    height: 300
  });
  const layer13 = new Konva.Layer();
  stage13.add(layer13);
  const rect15 = new Konva.Rect({
    x: 50,
    y: 50,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 4
  });
  layer13.add(rect15);
  rect15.on('click', function () {
    alert('rect15')
  });
  layer13.on('click', function () {
    alert('layer13')
  });
  // 空区域，只有stage会触发事件
  stage13.on('click', function () {
    alert('stage13')
  });
  /* 键盘事件 */
  const stage14 = new Konva.Stage({
    container: 'c14',
    width: 300,
    height: 300
  });
  const layer14 = new Konva.Layer();
  stage14.add(layer14);
  const rect16 = new Konva.Rect({
    x: 100,
    y: 100,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 4
  });
  layer14.add(rect16);
  const container = stage14.container();
  // 给stage设置tabIndex使其可以被focus，就可以监听键盘事件了
  container.tabIndex = 1;
  const DELTA = 5;
  container.addEventListener('keydown', function (e) {
    if (e.keyCode === 37) {
      rect16.x(rect16.x() - DELTA);
    } else if (e.keyCode === 38) {
      rect16.y(rect16.y() - DELTA);
    } else if (e.keyCode === 39) {
      rect16.x(rect16.x() + DELTA);
    } else if (e.keyCode === 40) {
      rect16.y(rect16.y() + DELTA);
    }
    // 阻止浏览器默认事件
    e.preventDefault();
  });
  /* 指针事件 */
  const stage15 = new Konva.Stage({
    container: 'c15',
    width: 300,
    height: 300
  });
  const layer15 = new Konva.Layer();
  stage15.add(layer15);
  const text11 = new Konva.Text({
    x: 10,
    y: 10,
    fontFamily: 'Calibri',
    fontSize: 24,
    text: '',
    fill: 'black'
  });
  layer15.add(text11);
  const triangle5 = new Konva.RegularPolygon({
    x: 80,
    y: 120,
    sides: 3,
    radius: 80,
    fill: '#00D2FF',
    stroke: 'black',
    strokeWidth: 4
  });
  layer15.add(triangle5);
  // 等同于 mousemove touchmove
  triangle5.on('pointermove', function () {
    const pos = stage15.getPointerPosition();
    text11.text('x: ' + pos.x + ', y: ' + pos.y);
  });
  const circle4 = new Konva.Circle({
    x: 230,
    y: 100,
    radius: 60,
    fill: 'red',
    stroke: 'black',
    strokeWidth: 4
  });
  layer15.add(circle4);
  // 等同于 mousedown touchstart
  circle4.on('pointerdown', function () {
    text11.text('按下');
  });
  // 等同于 mouseup touchend
  circle4.on('pointerup', function () {
    text11.text('抬起');
  });
  const rect17 = new Konva.Rect({
    x: 20,
    y: 180,
    width: 100,
    height: 100,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 4
  });
  layer15.add(rect17);
  // 等同于 click tap
  rect17.on('pointerclick', function () {
    text11.text('单击');
  });
  // 等同于 dblclick dbltap
  rect17.on('pointerdblclick ', function () {
    text11.text('双击');
  });
})
</script>
