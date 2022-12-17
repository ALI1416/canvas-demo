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
  /* 变形 */
  const stage = new Konva.Stage({
    container: 'c',
    width: 300,
    height: 300
  });
  const layer = new Konva.Layer();
  stage.add(layer);
  const rect1 = new Konva.Rect({
    x: 60,
    y: 60,
    width: 100,
    height: 60,
    fill: 'red',
    name: 'rect',
    draggable: true
  });
  layer.add(rect1);
  const rect2 = new Konva.Rect({
    x: 20,
    y: 150,
    width: 60,
    height: 100,
    fill: 'green',
    name: 'rect',
    draggable: true
  });
  layer.add(rect2);
  const rect3 = new Konva.Rect({
    x: 140,
    y: 150,
    width: 60,
    height: 100,
    fill: 'blue',
    name: 'rect',
    draggable: true
  });
  layer.add(rect3);
  // 创建一个变形示例
  const tr = new Konva.Transformer();
  layer.add(tr);
  // 选择图形
  tr.nodes([rect1, rect2]);
  // 绘制`选择矩形`，去选择图形
  const selectionRectangle = new Konva.Rect({
    fill: 'rgba(0,0,255,0.5)',
    visible: false,
  });
  layer.add(selectionRectangle);
  let x1, y1, x2, y2;
  // 记录`选择矩形`起点坐标
  stage.on('mousedown touchstart', (e) => {
    // 鼠标从图形上`按下`，跳过
    if (e.target !== stage) {
      return;
    }
    e.evt.preventDefault();
    // 记录起点坐标
    x1 = stage.getPointerPosition().x;
    y1 = stage.getPointerPosition().y;
    x2 = stage.getPointerPosition().x;
    y2 = stage.getPointerPosition().y;
    // 开始绘制`选择矩形`
    selectionRectangle.visible(true);
    selectionRectangle.width(0);
    selectionRectangle.height(0);
  });
  // 绘制`选择矩形`
  stage.on('mousemove touchmove', (e) => {
    // `选择矩形`没有显示，跳过
    if (!selectionRectangle.visible()) {
      return;
    }
    e.evt.preventDefault();
    // 记录中间点坐标
    x2 = stage.getPointerPosition().x;
    y2 = stage.getPointerPosition().y;
    // 绘制`选择矩形`
    selectionRectangle.setAttrs({
      x: Math.min(x1, x2),
      y: Math.min(y1, y2),
      width: Math.abs(x2 - x1),
      height: Math.abs(y2 - y1),
    });
  });
  // 选择被选中的图形
  stage.on('mouseup touchend', (e) => {
    // `选择矩形`没有显示，跳过
    if (!selectionRectangle.visible()) {
      return;
    }
    e.evt.preventDefault();
    // 延迟更新可见性，以便可以在单击事件中检查它
    setTimeout(() => {
      selectionRectangle.visible(false);
    });
    // 选中图形(仅选择矩形)
    let shapes = stage.find('.rect');
    let box = selectionRectangle.getClientRect();
    let selected = shapes.filter((shape) =>
        Konva.Util.haveIntersection(box, shape.getClientRect())
    );
    tr.nodes(selected);
  });
  // 选择/取消选择形状
  stage.on('click tap', function (e) {
    // `选择矩形`显示，跳过
    if (selectionRectangle.visible()) {
      return;
    }
    // 点击了空白区域，取消选择的图形
    if (e.target === stage) {
      tr.nodes([]);
      return;
    }
    // 选择的不是矩形，跳过
    if (!e.target.hasName('rect')) {
      return;
    }
    // 按下Ctrl或Shift键时，多选图形
    const metaPressed = e.evt.shiftKey || e.evt.ctrlKey || e.evt.metaKey;
    const isSelected = tr.nodes().indexOf(e.target) >= 0;
    if (!metaPressed && !isSelected) {
      // 没有按键、当前图形没有被选择过时：只选择当前被选中的图形
      tr.nodes([e.target]);
    } else if (metaPressed && isSelected) {
      // 按键、当前图形被选择过时：取消选择当前被选中的图形
      const nodes = tr.nodes().slice();
      nodes.splice(nodes.indexOf(e.target), 1);
      tr.nodes(nodes);
    } else if (metaPressed && !isSelected) {
      // 按键、当前图形没有被选择过时：选择当前被选中的图形
      const nodes = tr.nodes().concat([e.target]);
      tr.nodes(nodes);
    }
  });
  /* 从图形中心缩放 */
  const stage2 = new Konva.Stage({
    container: 'c2',
    width: 300,
    height: 300
  });
  const layer2 = new Konva.Layer();
  stage2.add(layer2);
  const text1 = new Konva.Text({
    x: 100,
    y: 70,
    fontSize: 50,
    text: 'true',
    draggable: true
  });
  layer2.add(text1);
  const tr1 = new Konva.Transformer({
    // 选择应用的图形
    nodes: [text1],
    // 从图形中心缩放
    centeredScaling: true
  });
  layer2.add(tr1);
  const text2 = new Konva.Text({
    x: 100,
    y: 200,
    fontSize: 50,
    text: 'false',
    draggable: true
  });
  layer2.add(text2);
  const tr2 = new Konva.Transformer({
    nodes: [text2],
    // 按住Alt键也可以实现为true的效果
    centeredScaling: false
  });
  layer2.add(tr2);
  /* 等比例缩放 */
  const stage3 = new Konva.Stage({
    container: 'c3',
    width: 300,
    height: 300
  });
  const layer3 = new Konva.Layer();
  stage3.add(layer3);
  const text3 = new Konva.Text({
    x: 100,
    y: 70,
    fontSize: 50,
    text: 'true',
    draggable: true
  });
  layer3.add(text3);
  const tr3 = new Konva.Transformer({
    nodes: [text3],
    // 等比例缩放：默认
    keepRatio: true,
    // 默认情况下拖动控件四个角上的控制点缩放是等比例的
    enabledAnchors: ['top-left', 'top-right', 'bottom-left', 'bottom-right']
  });
  layer3.add(tr3);
  const text4 = new Konva.Text({
    x: 100,
    y: 200,
    fontSize: 50,
    text: 'false',
    draggable: true
  });
  layer3.add(text4);
  const tr4 = new Konva.Transformer({
    nodes: [text4],
    // 按住Shift键也可以实现为true的效果
    keepRatio: false,
    enabledAnchors: ['top-left', 'top-right', 'bottom-left', 'bottom-right']
  });
  layer3.add(tr4);
  /* 样式 */
  const stage4 = new Konva.Stage({
    container: 'c4',
    width: 300,
    height: 300
  });
  const layer4 = new Konva.Layer();
  stage4.add(layer4);
  const circle = new Konva.Circle({
    x: 150,
    y: 150,
    radius: 70,
    fill: 'red',
    draggable: true
  });
  layer4.add(circle);
  const tr5 = new Konva.Transformer({
    // 锚点边框颜色
    anchorStroke: 'red',
    // 锚点填充颜色
    anchorFill: 'yellow',
    // 锚点宽度
    anchorSize: 20,
    // 边框颜色
    borderStroke: 'green',
    // 边框虚线
    borderDash: [3, 3]
  });
  layer4.add(tr5);
  // 指定应用于哪个图形
  tr5.nodes([circle]);
  /* 变形事件 */
  const stage5 = new Konva.Stage({
    container: 'c5',
    width: 300,
    height: 300
  });
  const layer5 = new Konva.Layer();
  stage5.add(layer5);
  const rect = new Konva.Rect({
    x: 150,
    y: 150,
    width: 100,
    height: 50,
    fill: 'red',
    stroke: 'black',
    draggable: true
  });
  layer5.add(rect);
  const text = new Konva.Text({
    x: 5,
    y: 5
  });
  layer5.add(text);
  updateText();
  const tr6 = new Konva.Transformer();
  layer5.add(tr6);
  tr6.nodes([rect]);
  rect.on('transformstart', function () {
    updateText('变形开始');
    console.log('transform start');
  });
  rect.on('dragmove', function () {
    updateText('拖拽');
  });
  rect.on('transform', function () {
    updateText('变形中');
  });
  rect.on('transformend', function () {
    updateText('变形结束');
  });

  function updateText(msg) {
    let lines = [
      'msg: ' + msg,
      'x: ' + rect.x(),
      'y: ' + rect.y(),
      'rotation: ' + rect.rotation(),
      'width: ' + rect.width(),
      'height: ' + rect.height(),
      'scaleX: ' + rect.scaleX(),
      'scaleY: ' + rect.scaleY()
    ];
    text.text(lines.join('\n'));
  }

  /* 限制缩放尺寸 */
  const stage6 = new Konva.Stage({
    container: 'c6',
    width: 300,
    height: 300
  });
  const layer6 = new Konva.Layer();
  stage6.add(layer6);
  const rect4 = new Konva.Rect({
    x: 100,
    y: 100,
    width: 50,
    height: 50,
    fill: 'red',
    stroke: 'black',
    draggable: true
  });
  layer6.add(rect4);
  const tr7 = new Konva.Transformer({
    // 限制边界
    boundBoxFunc: function (oldBoundBox, newBoundBox) {
      if (newBoundBox.width > 100) {
        return oldBoundBox;
      }
      return newBoundBox;
    }
  });
  layer6.add(tr7);
  tr7.nodes([rect4]);
  /* 旋转吸附 */
  const stage7 = new Konva.Stage({
    container: 'c7',
    width: 300,
    height: 300
  });
  const layer7 = new Konva.Layer();
  stage7.add(layer7);
  const text5 = new Konva.Text({
    x: 100,
    y: 100,
    fontSize: 30,
    text: '旋转',
    draggable: true
  });
  layer7.add(text5);
  const tr8 = new Konva.Transformer({
    nodes: [text5],
    centeredScaling: true,
    // 选择吸附点
    rotationSnaps: [0, 90, 180, 270],
    // 禁用调整大小
    resizeEnabled: false
  });
  layer7.add(tr8);
  /* 停止变形 */
  const stage8 = new Konva.Stage({
    container: 'c8',
    width: 300,
    height: 300
  });
  const layer8 = new Konva.Layer();
  stage8.add(layer8);
  const rect5 = new Konva.Rect({
    x: 100,
    y: 100,
    width: 50,
    height: 50,
    fill: 'red',
    stroke: 'black',
    draggable: true
  });
  layer8.add(rect5);
  const tr9 = new Konva.Transformer();
  layer8.add(tr9);
  tr9.nodes([rect5]);
  tr9.on('transform', function () {
    // 宽度大于100时停止变形
    if (rect5.width() * rect5.scaleX() > 100) {
      tr9.stopTransform();
      rect5.scaleX(100 / rect5.width());
    }
  });
  /* 强制更新 */
  const stage9 = new Konva.Stage({
    container: 'c9',
    width: 300,
    height: 280
  });
  const layer9 = new Konva.Layer();
  stage9.add(layer9);
  const group = new Konva.Group({
    x: 50,
    y: 50,
    draggable: true
  });
  layer9.add(group);
  const tr10 = new Konva.Transformer();
  layer9.add(tr10);
  tr10.nodes([group]);
  const c9 = document.getElementById('c9').firstElementChild;
  c9.style.display = 'inline-block';
  const btn = document.createElement('button');
  c9.before(btn);
  btn.innerText = "新增图形";
  btn.addEventListener('click', function () {
    group.add(
        new Konva.Circle({
          x: Math.random() * 100,
          y: Math.random() * 100,
          radius: Math.random() * 50,
          fill: Konva.Util.getRandomColor(),
          stroke: 'black',
          strokeWidth: Math.random() * 10
        })
    );
    // group无法监听，需要强制更新
    tr10.forceUpdate();
  })
  btn.click();
  /* 文字自动换行 */
  const stage10 = new Konva.Stage({
    container: 'c10',
    width: 300,
    height: 300
  });
  const layer10 = new Konva.Layer();
  stage10.add(layer10);
  const text6 = new Konva.Text({
    x: 50,
    y: 100,
    fontSize: 20,
    text: '拖拽调整文字自动换行',
    draggable: true,
  });
  layer10.add(text6);
  const tr11 = new Konva.Transformer({
    nodes: [text6],
    padding: 5,
    enabledAnchors: ['middle-left', 'middle-right'],
    boundBoxFunc: (oldBox, newBox) => {
      if (newBox.width < 20) {
        return oldBox;
      }
      return newBox;
    },
  });
  layer10.add(tr11);
  text6.on('transform', () => {
    text6.setAttrs({
      // 变形改变的是scale，文字scale只需重置为1，改变width即可
      width: Math.max(text6.width() * text6.scaleX(), 20),
      scaleX: 1,
      scaleY: 1,
    });
  });
  /* 不改变边框缩放 */
  const stage11 = new Konva.Stage({
    container: 'c11',
    width: 300,
    height: 300
  });
  const layer11 = new Konva.Layer();
  stage11.add(layer11);
  const rect6 = new Konva.Rect({
    x: 20,
    y: 20,
    width: 100,
    height: 100,
    draggable: true,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 5,
  });
  layer11.add(rect6);
  const tr12 = new Konva.Transformer({
    nodes: [rect6],
    padding: 5,
  });
  layer11.add(tr12);
  const rect7 = new Konva.Rect({
    x: 150,
    y: 150,
    width: 100,
    height: 100,
    draggable: true,
    fill: 'red',
    stroke: 'black',
    strokeWidth: 5,
    // 关闭边框缩放
    strokeScaleEnabled: false
  });
  layer11.add(rect7);
  const tr13 = new Konva.Transformer({
    nodes: [rect7],
    // 关闭边框缩放
    ignoreStroke: true,
    padding: 5,
  });
  layer11.add(tr13);
})
</script>
