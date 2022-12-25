<template>
  <div id="c" class="c"></div>
  <div id="c2" class="c">
    <div id="c2_2" style="height: 200px">请点击导入按钮</div>
  </div>
  <div id="c3" class="c"></div>
  <div id="c4" class="c">
    <div id="c4_2" style="height: 200px">请点击导入按钮</div>
  </div>
  <div id="c5" class="c"></div>
</template>

<script setup>
import Konva from "konva";
import {onMounted} from "vue"

onMounted(() => {
  /* 导出JSON */
  const stage = new Konva.Stage({
    container: 'c',
    width: 300,
    height: 200
  });
  const layer = new Konva.Layer();
  stage.add(layer);
  const rect = new Konva.Rect({
    x: 100,
    y: 100,
    width: 100,
    height: 60,
    fill: 'red',
    draggable: true
  });
  layer.add(rect);
  const c = document.getElementById('c').firstElementChild;
  c.style.display = 'inline-block';
  const btn = document.createElement('button');
  c.after(btn);
  btn.innerText = "导出";
  btn.addEventListener('click', function () {
    textarea.value = stage.toJSON();
  })
  const textarea = document.createElement('textarea');
  textarea.style.height = '100px';
  textarea.style.width = '250px';
  btn.after(textarea);
  /* 导入JSON */
  let stage2;
  const c2 = document.getElementById('c2').firstElementChild;
  c2.style.display = 'inline-block';
  const btn2 = document.createElement('button');
  c2.after(btn2);
  btn2.innerText = "导入";
  btn2.addEventListener('click', function () {
    stage2 = Konva.Node.create(textarea2.value, 'c2_2');
  })
  const textarea2 = document.createElement('textarea');
  textarea2.value = '{"attrs":{"width":300,"height":200},"className":"Stage","children":[{"attrs":{},"className":"Layer","children":[{"attrs":{"x":100,"y":100,"width":100,"height":60,"fill":"red","draggable":true},"className":"Rect"}]}]}';
  textarea2.style.height = '100px';
  textarea2.style.width = '250px';
  btn2.after(textarea2);
  /* 复杂导出 */
  const stage3 = new Konva.Stage({
    container: 'c3',
    width: 300,
    height: 200
  });
  const layer3 = new Konva.Layer();
  stage3.add(layer3);
  // 无法导出图片、事件等
  const imageObj = new Image();
  imageObj.src = 'img/苹果.png';
  imageObj.onload = function () {
    const appleImage = new Konva.Image({
      x: 20,
      y: 50,
      width: 100,
      height: 100,
      image: imageObj,
      draggable: true,
      id: 'appleImage'
    });
    layer3.add(appleImage);
    appleImage.on('click', function (e) {
      text.text('点击了苹果');
      e.cancelBubble = true;
    });
  };
  Konva.Image.fromURL('img/橘子.png', function (tangerineImage) {
    tangerineImage.setAttrs({
      x: 150,
      y: 100,
      scaleX: 0.2,
      scaleY: 0.2,
      draggable: true,
      id: 'tangerineImage'
    });
    layer3.add(tangerineImage);
    tangerineImage.on('click', function (e) {
      text.text('点击了橘子');
      e.cancelBubble = true;
    });
  });
  const text = new Konva.Text({
    x: 10,
    y: 10,
    fontFamily: 'Calibri',
    fontSize: 24,
    text: '文字',
    fill: 'black',
    id: 'text'
  });
  layer3.add(text);
  stage3.on('click', function () {
    text.text('');
  });
  const c3 = document.getElementById('c3').firstElementChild;
  c3.style.display = 'inline-block';
  const btn3 = document.createElement('button');
  c3.after(btn3);
  btn3.innerText = "导出";
  btn3.addEventListener('click', function () {
    textarea3.value = stage3.toJSON();
  })
  const textarea3 = document.createElement('textarea');
  textarea3.style.height = '100px';
  textarea3.style.width = '250px';
  btn3.after(textarea3);
  /* 复杂导入 */
  let stage4;
  const c4 = document.getElementById('c4').firstElementChild;
  c4.style.display = 'inline-block';
  const btn4 = document.createElement('button');
  c4.after(btn4);
  btn4.innerText = "导入";
  btn4.addEventListener('click', function () {
    stage4 = Konva.Node.create(textarea4.value, 'c4_2');
    // 手动设置图片、事件
    let text2 = stage4.findOne('#text');
    let imageObj2 = new Image();
    imageObj2.src = 'img/苹果.png';
    imageObj2.onload = function () {
      let appleImage = stage4.findOne('#appleImage');
      appleImage.image(imageObj2);
      appleImage.on('click', function (e) {
        text2.text('点击了苹果');
        e.cancelBubble = true;
      });
    };
    Konva.Image.fromURL('img/橘子.png', function (tangerineImage) {
      let tangerineImage2 = stage4.findOne('#tangerineImage');
      tangerineImage2.image(tangerineImage.image());
      tangerineImage2.on('click', function (e) {
        text2.text('点击了橘子');
        e.cancelBubble = true;
      });
    });
    stage4.on('click', function () {
      text2.text('');
    });
  })
  const textarea4 = document.createElement('textarea');
  textarea4.value = '{"attrs":{"width":300,"height":200},"className":"Stage","children":[{"attrs":{},"className":"Layer","children":[{"attrs":{"x":10,"y":10,"fontFamily":"Calibri","fontSize":24,"text":"文字","fill":"black","id":"text"},"className":"Text"},{"attrs":{"x":20,"y":50,"width":100,"height":100,"draggable":true,"id":"appleImage"},"className":"Image"},{"attrs":{"x":150,"y":100,"scaleX":0.2,"scaleY":0.2,"draggable":true,"id":"tangerineImage"},"className":"Image"}]}]}';
  textarea4.style.height = '100px';
  textarea4.style.width = '250px';
  btn4.after(textarea4);
  /* 导出 */
  const stage5 = new Konva.Stage({
    container: 'c5',
    width: 300,
    height: 280
  });
  const layer5 = new Konva.Layer();
  stage5.add(layer5);
  const rect3 = new Konva.Rect({
    x: 100,
    y: 100,
    width: 100,
    height: 60,
    fill: 'red',
    draggable: true
  });
  layer5.add(rect3);
  const c5 = document.getElementById('c5').firstElementChild;
  c5.style.display = 'inline-block';
  const btn5 = document.createElement('button');
  c5.before(btn5);
  btn5.innerText = "普通导出";
  btn5.addEventListener('click', function () {
    downLoad(stage5.toDataURL())
  });
  const btn6 = document.createElement('button');
  c5.before(btn6);
  btn6.innerText = "缩放导出";
  btn6.addEventListener('click', function () {
    downLoad(stage5.toDataURL({pixelRatio: 2}))
  });
})

// 下载
function downLoad(url) {
  const a = document.createElement("a");
  a.download = '';
  a.href = url;
  document.body.appendChild(a);
  a.click();
  a.remove();
}

</script>
