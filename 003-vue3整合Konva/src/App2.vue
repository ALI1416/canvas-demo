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
  <div id="c16" class="c"></div>
  <div id="c17" class="c"></div>
  <div id="c18" class="c"></div>
  <div id="c19" class="c"></div>
</template>

<script setup>
import Konva from "konva";
import {onMounted} from "vue"

onMounted(() => {
  /* 圆 */
  const stage = new Konva.Stage({
    container: 'c',
    width: 300,
    height: 300
  });
  const layer = new Konva.Layer();
  stage.add(layer);
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
  layer.add(circle);
  /* 矩形 */
  const stage2 = new Konva.Stage({
    container: 'c2',
    width: 300,
    height: 300
  });
  const layer2 = new Konva.Layer();
  stage2.add(layer2);
  const rect1 = new Konva.Rect({
    x: 20,
    y: 20,
    width: 100,
    height: 50,
    fill: 'green',
    stroke: 'black',
    strokeWidth: 4
  });
  layer2.add(rect1);
  const rect2 = new Konva.Rect({
    x: 150,
    y: 40,
    width: 100,
    height: 50,
    fill: 'red',
    // 阴影模糊程度
    shadowBlur: 10,
    // 圆角半径
    cornerRadius: 10
  });
  layer2.add(rect2);
  const rect3 = new Konva.Rect({
    x: 50,
    y: 120,
    width: 100,
    height: 100,
    fill: 'blue',
    // 圆角半径(从左上角 顺时针)
    cornerRadius: [0, 10, 20, 30]
  });
  layer2.add(rect3);
  /* 椭圆 */
  const stage3 = new Konva.Stage({
    container: 'c3',
    width: 300,
    height: 300
  });
  const layer3 = new Konva.Layer();
  stage3.add(layer3);
  const ellipse = new Konva.Ellipse({
    x: stage.width() / 2,
    y: stage.height() / 2,
    // X轴半径
    radiusX: 100,
    // Y轴半径
    radiusY: 50,
    fill: 'yellow',
    stroke: 'black',
    strokeWidth: 4
  });
  layer3.add(ellipse);
  /* 扇形 */
  const stage4 = new Konva.Stage({
    container: 'c4',
    width: 300,
    height: 300
  });
  const layer4 = new Konva.Layer();
  stage4.add(layer4);
  const wedge = new Konva.Wedge({
    x: stage.width() / 2,
    y: stage.height() / 2,
    // 半径
    radius: 70,
    // 扇形角度
    angle: 60,
    fill: 'red',
    stroke: 'black',
    strokeWidth: 4,
    // 旋转角度(X轴正半轴为0度 顺时针)
    rotation: -30
  });
  layer4.add(wedge);
  /* 简单线条 */
  const stage5 = new Konva.Stage({
    container: 'c5',
    width: 300,
    height: 300
  });
  const layer5 = new Konva.Layer();
  stage5.add(layer5);
  const redLine = new Konva.Line({
    // xy坐标：每2个为一组
    points: [15, 70, 140, 23, 250, 60, 280, 20],
    stroke: 'red',
    strokeWidth: 15,
    // 末端样式
    lineCap: 'round',
    // 拐点样式
    lineJoin: 'round'
  });
  const greenLine = new Konva.Line({
    points: [15, 70, 140, 23, 250, 60, 280, 20],
    stroke: 'green',
    strokeWidth: 2,
    lineJoin: 'round',
    // 虚线
    dash: [33, 10]
  });
  // 移动位置
  redLine.move({
    x: 0,
    y: 50
  });
  greenLine.move({
    x: 0,
    y: 100
  });
  layer5.add(redLine);
  layer5.add(greenLine);
  /* 多边形 */
  const stage6 = new Konva.Stage({
    container: 'c6',
    width: 300,
    height: 300
  });
  const layer6 = new Konva.Layer();
  stage6.add(layer6);
  const polygon = new Konva.Line({
    points: [23, 20, 23, 160, 70, 93, 150, 109, 290, 139, 270, 93],
    fill: '#00D2FF',
    stroke: 'black',
    strokeWidth: 5,
    // 闭合路径
    closed: true
  });
  layer6.add(polygon);
  /* 样条曲线 */
  const stage7 = new Konva.Stage({
    container: 'c7',
    width: 300,
    height: 300
  });
  const layer7 = new Konva.Layer();
  stage7.add(layer7);
  const blueLine = new Konva.Line({
    points: [15, 70, 140, 23, 250, 60, 280, 20],
    stroke: 'blue',
    strokeWidth: 10,
    lineCap: 'round',
    lineJoin: 'round',
    // 拉紧程度
    tension: 0.7
  });
  blueLine.move({
    x: 0,
    y: 100
  });
  layer7.add(blueLine);
  /* blob图形 */
  const stage8 = new Konva.Stage({
    container: 'c8',
    width: 300,
    height: 300
  });
  const layer8 = new Konva.Layer();
  stage8.add(layer8);
  const blob = new Konva.Line({
    points: [23, 20, 23, 160, 70, 93, 150, 109, 290, 139, 270, 93],
    fill: '#00D2FF',
    stroke: 'black',
    strokeWidth: 5,
    closed: true,
    tension: 0.3
  });
  layer8.add(blob);
  /* 加载图片 */
  const stage9 = new Konva.Stage({
    container: 'c9',
    width: 300,
    height: 300
  });
  const layer9 = new Konva.Layer();
  stage9.add(layer9);
  // 使用原生Image
  const imageObj = new Image();
  imageObj.src = 'img/苹果.png';
  imageObj.onload = function () {
    const appleImage = new Konva.Image({
      x: 20,
      y: 20,
      width: 100,
      height: 100,
      image: imageObj
    });
    layer9.add(appleImage);
  };
  // 使用Konva的Image
  Konva.Image.fromURL('img/橘子.png', function (tangerineImage) {
    tangerineImage.setAttrs({
      x: 150,
      y: 150,
      // X轴缩放
      scaleX: 0.5,
      // Y轴缩放
      scaleY: 0.5
    });
    layer9.add(tangerineImage);
  });
  /* 文字 */
  const stage10 = new Konva.Stage({
    container: 'c10',
    width: 300,
    height: 300
  });
  const layer10 = new Konva.Layer();
  stage10.add(layer10);
  // 普通文字
  const simpleText = new Konva.Text({
    x: stage10.width() / 2,
    y: 15,
    // 文本
    text: 'Simple Text',
    // 字号
    fontSize: 30,
    // 字体
    fontFamily: 'Calibri',
    fill: 'green'
  });
  // 设置偏移
  simpleText.offsetX(simpleText.width() / 2);
  // 复杂文字
  const complexText = new Konva.Text({
    x: 20,
    y: 60,
    text:
        "COMPLEX TEXT\n\nAll the world's a stage, and all the men and women merely players. They have their exits and their entrances.",
    fontSize: 18,
    fontFamily: 'Calibri',
    fill: '#555',
    width: 250,
    // 间距
    padding: 20,
    // 格式
    align: 'center'
  });
  // 文字边框
  const rectText = new Konva.Rect({
    x: 20,
    y: 60,
    stroke: '#555',
    strokeWidth: 5,
    fill: '#ddd',
    width: 250,
    height: complexText.height(),
    shadowColor: 'black',
    shadowBlur: 10,
    shadowOffsetX: 10,
    shadowOffsetY: 10,
    shadowOpacity: 0.2,
    cornerRadius: 10
  });
  layer10.add(simpleText);
  layer10.add(rectText);
  layer10.add(complexText);
  /* 路径文字 */
  const stage11 = new Konva.Stage({
    container: 'c11',
    width: 300,
    height: 300
  });
  const layer11 = new Konva.Layer();
  stage11.add(layer11);
  const textpath = new Konva.TextPath({
    x: 0,
    y: 50,
    fill: '#333',
    fontSize: 16,
    fontFamily: 'Arial',
    text:
        "All the world's a stage, and all the men and women merely players.",
    // SVG path 路径
    data: 'M10,10 C0,0 10,150 100,100 S300,150 4.0.180'
  });
  layer11.add(textpath);
  /* 星形 */
  const stage12 = new Konva.Stage({
    container: 'c12',
    width: 300,
    height: 300
  });
  const layer12 = new Konva.Layer();
  stage12.add(layer12);
  const star = new Konva.Star({
    x: stage12.width() / 2,
    y: stage12.height() / 2,
    // 角的个数
    numPoints: 6,
    // 内部半径
    innerRadius: 40,
    // 外部半径
    outerRadius: 70,
    fill: 'yellow',
    stroke: 'black',
    strokeWidth: 4
  });
  layer12.add(star);
  /* 环形 */
  const stage13 = new Konva.Stage({
    container: 'c13',
    width: 300,
    height: 300
  });
  const layer13 = new Konva.Layer();
  stage13.add(layer13);
  const ring = new Konva.Ring({
    x: stage13.width() / 2,
    y: stage13.height() / 2,
    // 内部半径
    innerRadius: 40,
    // 外部半径
    outerRadius: 70,
    fill: 'yellow',
    stroke: 'black',
    strokeWidth: 4
  });
  layer13.add(ring);
  /* 弧形 */
  const stage14 = new Konva.Stage({
    container: 'c14',
    width: 300,
    height: 300
  });
  const layer14 = new Konva.Layer();
  stage14.add(layer14);
  const arc = new Konva.Arc({
    x: stage14.width() / 2,
    y: stage14.height() / 2,
    // 内部半径
    innerRadius: 40,
    // 外部半径
    outerRadius: 70,
    // 角度
    angle: 60,
    fill: 'yellow',
    stroke: 'black',
    strokeWidth: 4
  });
  layer14.add(arc);
  /* 标签 */
  const stage15 = new Konva.Stage({
    container: 'c15',
    width: 300,
    height: 300
  });
  const layer15 = new Konva.Layer();
  stage15.add(layer15);
// 创建一个提示
  const tooltip = new Konva.Label({
    x: 170,
    y: 75,
    // 透明度
    opacity: 0.75
  });
  tooltip.add(
      // 箭头
      new Konva.Tag({
        fill: 'black',
        // 箭头方向
        pointerDirection: 'down',
        // 箭头宽度
        pointerWidth: 10,
        // 箭头高度
        pointerHeight: 10,
        lineJoin: 'round',
        shadowColor: 'black',
        shadowBlur: 10,
        shadowOffsetX: 10,
        shadowOffsetY: 10,
        shadowOpacity: 0.5
      })
  );
  tooltip.add(
      // 显示文字
      new Konva.Text({
        text: 'Tooltip pointing down',
        fontFamily: 'Calibri',
        fontSize: 18,
        padding: 5,
        fill: 'white'
      })
  );
  // 创建一个左侧标签
  const labelLeft = new Konva.Label({
    x: 20,
    y: 130,
    opacity: 0.75
  });
  labelLeft.add(
      new Konva.Tag({
        fill: 'green',
        pointerDirection: 'left',
        pointerWidth: 20,
        pointerHeight: 28,
        lineJoin: 'round'
      })
  );
  labelLeft.add(
      new Konva.Text({
        text: 'Label pointing left',
        fontFamily: 'Calibri',
        fontSize: 18,
        padding: 5,
        fill: 'white'
      })
  );
  // 创建一个普通标签
  const simpleLabel = new Konva.Label({
    x: 180,
    y: 150,
    opacity: 0.75
  });
  simpleLabel.add(
      new Konva.Tag({
        fill: 'yellow'
      })
  );
  simpleLabel.add(
      new Konva.Text({
        text: 'Simple label',
        fontFamily: 'Calibri',
        fontSize: 18,
        padding: 5,
        fill: 'black'
      })
  );
  layer15
      .add(tooltip)
      .add(labelLeft)
      .add(simpleLabel);
  /* 路径 */
  const stage16 = new Konva.Stage({
    container: 'c16',
    width: 300,
    height: 300
  });
  const layer16 = new Konva.Layer();
  stage16.add(layer16);
  const path = new Konva.Path({
    x: 50,
    y: 40,
    data:
        'M12.582,9.551C3.251,16.237,0.921,29.021,7.08,38.564l-2.36,1.689l4.893,2.262l4.893,2.262l-0.568-5.36l-0.567-5.359l-2.365,1.694c-4.657-7.375-2.83-17.185,4.352-22.33c7.451-5.338,17.817-3.625,23.156,3.824c5.337,7.449,3.625,17.813-3.821,23.152l2.857,3.988c9.617-6.893,11.827-20.277,4.935-29.896C35.591,4.87,22.204,2.658,12.582,9.551z',
    fill: 'green',
    scale: {
      x: 2,
      y: 2
    }
  });
  layer16.add(path);
  /* 等边多边形 */
  const stage17 = new Konva.Stage({
    container: 'c17',
    width: 300,
    height: 300
  });
  const layer17 = new Konva.Layer();
  stage17.add(layer17);
  const regularPolygon = new Konva.RegularPolygon({
    x: 100,
    y: 150,
    // 边数
    sides: 6,
    // 半径
    radius: 70,
    fill: 'red',
    stroke: 'black',
    strokeWidth: 4
  });
  layer17.add(regularPolygon);
  /* 箭头 */
  const stage18 = new Konva.Stage({
    container: 'c18',
    width: 300,
    height: 300
  });
  const layer18 = new Konva.Layer();
  stage18.add(layer18);
  const arrow = new Konva.Arrow({
    x: stage.width() / 4,
    y: stage.height() / 4,
    // 起点XY,终点XY
    points: [0, 0, 100, 100],
    // 箭头长度
    pointerLength: 20,
    // 箭头宽度
    pointerWidth: 20,
    fill: 'black',
    stroke: 'black',
    strokeWidth: 4
  });
  layer18.add(arrow);
  /* 自定义图形 */
  const stage19 = new Konva.Stage({
    container: 'c19',
    width: 300,
    height: 300
  });
  const layer19 = new Konva.Layer();
  stage19.add(layer19);
  const triangle = new Konva.Shape({
    sceneFunc: function (context, shape) {
      context.beginPath();
      context.moveTo(20, 50);
      context.lineTo(220, 80);
      context.quadraticCurveTo(150, 100, 260, 170);
      context.closePath();
      // 自动填充轮廓
      context.fillStrokeShape(shape);
    },
    fill: '#00D2FF',
    stroke: 'black',
    strokeWidth: 4
  });
  layer19.add(triangle);

})
</script>
