<template>
  <div style="display: inline-block;width: 300px;">
    <div>
      <input id="blurCb" type="checkbox"/>模糊
      <input id="blur" type="range" min="0" max="50" step="0.1" value="0"/>
      <span id="blurV">0</span>
    </div>
    <div>
      <input type="checkbox"/>模糊
      <input id="slider" type="range" min="0" max="40" step="0.05" value="00"/>
    </div>
  </div>
  <div id="c" class="c">0</div>
</template>

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
    lion.cache();
    // 模糊
    document.getElementById('blurCb').onchange = function (e) {
      filterChange(e.target.checked, Konva.Filters.Blur);
    }
    document.getElementById('blur').oninput = function (e) {
      const value = e.target.value;
      document.getElementById('blurV').innerText = value;
      lion.blurRadius(Number(value));
    }

    // 滤镜修改
    function filterChange(add, filters) {
      if (add) {
        lion.filters([filters]);
      } else {
        lion.filters(lion.filters().filter((i) => i !== filters));
      }
    }
  });
})

</script>

