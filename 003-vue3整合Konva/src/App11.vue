<template>
  <div id="c" class="c" style="width: 420px;height: 420px"></div>
</template>

<script setup>
import Konva from "konva";
import {onMounted} from "vue"

onMounted(() => {
  /* 选择器 */
  const stage = new Konva.Stage({
    container: 'c',
    width: 420,
    height: 400
  });
  const layer = new Konva.Layer();
  stage.add(layer);
  for (let n = 0; n < 10; n++) {
    let circle = new Konva.Circle({
      x: Math.random() * stage.width(),
      y: Math.random() * stage.height(),
      radius: Math.random() * 50 + 25,
      fill: 'red',
      strokeWidth: 2,
      stroke: 'black'
    });
    layer.add(circle);
  }
  let rect = new Konva.Rect({
    x: 140,
    y: 120,
    width: 80,
    height: 40,
    fill: 'green',
    offset: {
      x: 40,
      y: 20
    },
    draggable: true,
    // 设置id
    id: 'greenRect'
  });
  layer.add(rect);
  let rect2 = new Konva.Rect({
    x: 340,
    y: 120,
    width: 80,
    height: 40,
    fill: 'blue',
    offset: {
      x: 40,
      y: 20
    },
    draggable: true,
  });
  layer.add(rect2);
  let rect3 = new Konva.Rect({
    x: 340,
    y: 220,
    width: 80,
    height: 40,
    fill: 'blue',
    offset: {
      x: 40,
      y: 20
    },
    draggable: true,
  });
  layer.add(rect3);
  let rect4 = new Konva.Rect({
    x: 140,
    y: 220,
    width: 80,
    height: 40,
    fill: 'yellow',
    offset: {
      x: 40,
      y: 20
    },
    draggable: true,
    // 设置name
    name: 'yellowRect'
  });
  layer.add(rect4);
  const c = document.getElementById('c').firstElementChild;
  c.style.display = 'inline-block';
  const btn_id = document.createElement('button');
  c.before(btn_id);
  btn_id.innerText = "绿色矩形";
  btn_id.addEventListener('click', function () {
    // 通过id查找
    // 或者stage.findOne('#greenRect');
    let shapes = stage.find('#greenRect');
    find(shapes);
  });
  const btn_name = document.createElement('button');
  c.before(btn_name);
  btn_name.innerText = "黄色矩形";
  btn_name.addEventListener('click', function () {
    // 通过name查找
    let shapes = stage.find('.yellowRect');
    find(shapes);
  });
  const btn_type = document.createElement('button');
  c.before(btn_type);
  btn_type.innerText = "矩形";
  btn_type.addEventListener('click', function () {
    // 通过类型查找
    let shapes = stage.find('Rect');
    find(shapes);
  });
})

let tweens = [];

function find(shapes) {
  tweens.forEach(function (tween) {
    tween.destroy();
  })
  shapes.forEach(function (shape) {
    tweens.push(
        new Konva.Tween({
          node: shape,
          duration: 1,
          scaleX: Math.random() * 2,
          scaleY: Math.random() * 2,
          easing: Konva.Easings.ElasticEaseOut
        }).play()
    )
  })
}
</script>
