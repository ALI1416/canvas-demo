<template>
  <div class="d">
    <div>
      <input id="blurCb" type="checkbox"/>模糊度
      <input id="blur" type="range" min="0" max="50" step="0.1" value="0"/>
      <span id="blurV">0</span>
    </div>
    <div>
      <input id="brightenCb" type="checkbox"/>亮度
      <input id="brighten" type="range" min="-1" max="1" step="0.01" value="0"/>
      <span id="brightenV">0</span>
    </div>
    <div>
      <input id="contrastCb" type="checkbox"/>对比度
      <input id="contrast" type="range" min="-100" max="100" step="0.1" value="0"/>
      <span id="contrastV">0</span>
    </div>
    <div>
      <input id="enhanceCb" type="checkbox"/>反差
      <input id="enhance" type="range" min="-1" max="1" step="0.01" value="0"/>
      <span id="enhanceV">0</span>
    </div>
    <div>
      <input id="maskCb" type="checkbox"/>遮罩
      <input id="mask" type="range" min="-1" max="360" step="1" value="0"/>
      <span id="maskV">0</span>
    </div>
    <div>
      <input id="noiseCb" type="checkbox"/>噪声
      <input id="noise" type="range" min="0" max="5" step="0.01" value="0.2"/>
      <span id="noiseV">0.2</span>
    </div>
    <div>
      <input id="pixelateCb" type="checkbox"/>像素化
      <input id="pixelate" type="range" min="1" max="20" step="1" value="8"/>
      <span id="pixelateV">8</span>
    </div>
    <div>
      <input id="posterizeCb" type="checkbox"/>色调分离
      <input id="posterize" type="range" min="0" max="1" step="0.01" value="0.5"/>
      <span id="posterizeV">0.5</span>
    </div>
    <div>
      <input id="thresholdCb" type="checkbox"/>临界点
      <input id="threshold" type="range" min="0" max="1" step="0.01" value="0"/>
      <span id="thresholdV">0</span>
    </div>
    <div>
      <input id="sepiaCb" type="checkbox"/>棕褐色
    </div>
    <div>
      <input id="solarizeCb" type="checkbox"/>曝光
    </div>
    <div>
      <input id="grayscaleCb" type="checkbox"/>灰度
    </div>
    <div>
      <input id="invertCb" type="checkbox"/>反相
    </div>
    <div>
      <input id="customFilterCb" type="checkbox"/>自定义滤镜
    </div>
  </div>
  <div class="d">
    <div>
      <input id="hslCb" type="checkbox"/>HSL
      <br>
      色相：<input id="hslHue" type="range" min="0" max="359" step="1" value="0"/>
      <span id="hslHueV">0</span>
      <br>
      饱和度：<input id="hslSaturation" type="range" min="-2" max="2" step="0.01" value="0"/>
      <span id="hslSaturationV">0</span>
      <br>
      亮度：<input id="hslLuminance" type="range" min="-2" max="2" step="0.01" value="0"/>
      <span id="hslLuminanceV">0</span>
    </div>
    <hr>
    <div>
      <input id="hsvCb" type="checkbox"/>HSV
      <br>
      色相：<input id="hsvHue" type="range" min="0" max="359" step="1" value="0"/>
      <span id="hsvHueV">0</span>
      <br>
      饱和度：<input id="hsvSaturation" type="range" min="-2" max="10" step="0.01" value="0"/>
      <span id="hsvSaturationV">0</span>
      <br>
      明度：<input id="hsvValue" type="range" min="-2" max="2" step="0.01" value="0"/>
      <span id="hsvValueV">0</span>
    </div>
  </div>
  <div class="d">
    <div>
      <input id="rgbCb" type="checkbox"/>RGB
      <br>
      红色：<input id="rgbRed" type="range" min="0" max="255" step="1" value="0"/>
      <span id="rgbRedV">0</span>
      <br>
      绿色：<input id="rgbGreen" type="range" min="0" max="255" step="1" value="0"/>
      <span id="rgbGreenV">0</span>
      <br>
      蓝色：<input id="rgbBlue" type="range" min="0" max="255" step="1" value="0"/>
      <span id="rgbBlueV">0</span>
    </div>
    <hr>
    <div>
      <input id="rgbaCb" type="checkbox"/>RGBA
      <br>
      红色：<input id="rgbaRed" type="range" min="0" max="255" step="1" value="0"/>
      <span id="rgbaRedV">0</span>
      <br>
      绿色：<input id="rgbaGreen" type="range" min="0" max="255" step="1" value="0"/>
      <span id="rgbaGreenV">0</span>
      <br>
      蓝色：<input id="rgbaBlue" type="range" min="0" max="255" step="1" value="0"/>
      <span id="rgbaBlueV">0</span>
      <br>
      透明：<input id="rgbaAlpha" type="range" min="0" max="1" step="0.01" value="1"/>
      <span id="rgbaAlphaV">1</span>
    </div>
  </div>
  <div class="d">
    <div>
      <input id="embossCb" type="checkbox"/>浮雕
      <br>
      方向：<input type="radio" name="embossDirectionR" value="top">上
      <input type="radio" name="embossDirectionR" value="bottom">下
      <input type="radio" name="embossDirectionR" value="left">左
      <input type="radio" name="embossDirectionR" value="right">右
      <br>
      <input type="radio" name="embossDirectionR" value="top-left" checked>左上
      <input type="radio" name="embossDirectionR" value="top-right">右上
      <input type="radio" name="embossDirectionR" value="bottom-left">左下
      <input type="radio" name="embossDirectionR" value="bottom-right">右下
      <br>
      混合：<input id="embossBlendCb" type="checkbox"/>
      <br>
      强度：<input id="embossStrength" type="range" min="0" max="1" step="0.01" value="0.5"/>
      <span id="embossStrengthV">0.5</span>
      <br>
      白度：<input id="embossWhiteLevel" type="range" min="0" max="1" step="0.01" value="0.5"/>
      <span id="embossWhiteLevelV">0.5</span>
    </div>
    <hr>
    <div>
      <input id="kaleidoscopeCb" type="checkbox"/>万花筒
      <br>
      幂次：<input id="kaleidoscopePower" type="range" min="0" max="3" step="1" value="2"/>
      <span id="kaleidoscopePowerV">2</span>
      <br>
      角度：<input id="kaleidoscopeAngle" type="range" min="0" max="360" step="1" value="0"/>
      <span id="kaleidoscopeAngleV">0</span>
    </div>
  </div>
  <hr>
  <div id="c" class="c"></div>
</template>

<style>
.d {
  width: 300px;
  display: inline-block;
  margin: 5px;
}
</style>

<script setup>
import Konva from "konva";
import {onMounted} from "vue"

onMounted(() => {
  const stage = new Konva.Stage({
    container: 'c',
    width: 300,
    height: 300
  });
  const layer = new Konva.Layer();
  stage.add(layer);
  Konva.Image.fromURL('img/狮子.png', function (lion) {
    lion.setAttrs({
      x: 0,
      y: 0,
      scaleX: 2,
      scaleY: 2
    });
    layer.add(lion);
    lion.filters([]);
    // 模糊
    document.getElementById('blurCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.Blur);
    }
    document.getElementById('blur').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('blurV').innerText = value;
      lion.blurRadius(Number(value));
    }
    // 亮度
    document.getElementById('brightenCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.Brighten);
    }
    document.getElementById('brighten').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('brightenV').innerText = value;
      lion.brightness(Number(value));
    }
    // 对比度
    document.getElementById('contrastCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.Contrast);
    }
    document.getElementById('contrast').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('contrastV').innerText = value;
      lion.contrast(Number(value));
    }
    // 浮雕
    document.getElementById('embossCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.Emboss);
    }
    document.getElementsByName('embossDirectionR').forEach(function (v) {
      v.onchange = function (e) {
        lion.embossDirection(e.target.value);
      }
    })
    document.getElementById('embossBlendCb').onchange = function (e) {
      lion.embossBlend(e.target.checked);
    }
    document.getElementById('embossStrength').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('embossStrengthV').innerText = value;
      lion.embossStrength(Number(value));
    }
    document.getElementById('embossWhiteLevel').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('embossWhiteLevelV').innerText = value;
      lion.embossWhiteLevel(Number(value));
    }
    // 反差
    document.getElementById('enhanceCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.Enhance);
    }
    document.getElementById('enhance').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('enhanceV').innerText = value;
      lion.enhance(Number(value));
    }
    // 灰度
    document.getElementById('grayscaleCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.Grayscale);
    }
    // HSL
    document.getElementById('hslCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.HSL);
    }
    document.getElementById('hslHue').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('hslHueV').innerText = value;
      lion.hue(Number(value));
    }
    document.getElementById('hslSaturation').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('hslSaturationV').innerText = value;
      lion.saturation(Number(value));
    }
    document.getElementById('hslLuminance').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('hslLuminanceV').innerText = value;
      lion.luminance(Number(value));
    }
    // HSV
    document.getElementById('hsvCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.HSV);
    }
    document.getElementById('hsvHue').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('hsvHueV').innerText = value;
      lion.hue(Number(value));
    }
    document.getElementById('hsvSaturation').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('hsvSaturationV').innerText = value;
      lion.saturation(Number(value));
    }
    document.getElementById('hsvValue').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('hsvValueV').innerText = value;
      lion.value(Number(value));
    }
    // 反相
    document.getElementById('invertCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.Invert);
    }
    // 万花筒
    document.getElementById('kaleidoscopeCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.Kaleidoscope);
    }
    document.getElementById('kaleidoscopePower').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('kaleidoscopePowerV').innerText = value;
      lion.kaleidoscopePower(Number(value));
    }
    document.getElementById('kaleidoscopeAngle').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('kaleidoscopeAngleV').innerText = value;
      lion.kaleidoscopeAngle(Number(value));
    }
    // 遮罩
    document.getElementById('maskCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.Mask);
    }
    document.getElementById('mask').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('maskV').innerText = value;
      lion.threshold(Number(value));
    }
    // 噪声
    document.getElementById('noiseCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.Noise);
    }
    document.getElementById('noise').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('noiseV').innerText = value;
      lion.noise(Number(value));
    }
    // 像素化
    document.getElementById('pixelateCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.Pixelate);
    }
    document.getElementById('pixelate').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('pixelateV').innerText = value;
      lion.pixelSize(Number(value));
    }
    // 色调分离
    document.getElementById('posterizeCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.Posterize);
    }
    document.getElementById('posterize').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('posterizeV').innerText = value;
      lion.levels(Number(value));
    }
    // RGB
    document.getElementById('rgbCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.RGB);
    }
    document.getElementById('rgbRed').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('rgbRedV').innerText = value;
      lion.red(Number(value));
    }
    document.getElementById('rgbGreen').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('rgbGreenV').innerText = value;
      lion.green(Number(value));
    }
    document.getElementById('rgbBlue').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('rgbBlueV').innerText = value;
      lion.blue(Number(value));
    }
    // RGBA
    document.getElementById('rgbaCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.RGBA);
    }
    document.getElementById('rgbaRed').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('rgbaRedV').innerText = value;
      lion.red(Number(value));
    }
    document.getElementById('rgbaGreen').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('rgbaGreenV').innerText = value;
      lion.green(Number(value));
    }
    document.getElementById('rgbaBlue').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('rgbaBlueV').innerText = value;
      lion.blue(Number(value));
    }
    document.getElementById('rgbaAlpha').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('rgbaAlphaV').innerText = value;
      lion.alpha(Number(value));
    }
    // 棕褐色
    document.getElementById('sepiaCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.Sepia);
    }
    // 曝光
    document.getElementById('solarizeCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.Solarize);
    }
    // 临界点
    document.getElementById('thresholdCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.Threshold);
    }
    document.getElementById('threshold').oninput = function (e) {
      let value = e.target.value;
      document.getElementById('thresholdV').innerText = value;
      lion.threshold(Number(value));
    }
    // 自定义滤镜
    document.getElementById('customFilterCb').onchange = function (e) {
      filterChange(e.target.checked, CustomFilter);
    }

    // 滤镜修改
    function filterChange(add, filters) {
      if (add) {
        lion.cache();
        lion.filters().push(filters);
      } else {
        lion.filters(lion.filters().filter((i) => i !== filters));
      }
    }

    // 自定义滤镜
    function CustomFilter(imageData) {
      for (let i = 0; i < imageData.data.length; i++) {
        imageData.data[i] = imageData.data[i] / 2;
      }
    }
  });
})

</script>

