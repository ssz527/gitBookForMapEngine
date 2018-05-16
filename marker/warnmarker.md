# 报警点位操作

## warnMarkerStart

> <font color=#00aa00>在 v3.0 中已实现</font>

```javascript
/**
 * 开启报警点位
 * @param {Object} warnInfo : 点位信息,对象
 * @param {Function} fn : 自定义样式，选填
 * {
 *  position: [0,0], 必填
 *  id: '111', 必填
 *  type: 'warn' || 'danger', 默认warn
 *  text: '落水预警', 默认'报警事件'
 *  color: '100,100,100' 自定义动画颜色，当传入color，type不起作用
 * }
 */
  warnMarkerStart(warnInfo, fn)
```

## warnMarkerCancel

> <font color=#00aa00>在 v3.0 中已实现</font>

```javascript
/**
 * 解除点位报警
 * @param {Object} warnInfo : 点位信息,对象
 * 参数示例：

 */
  warnMarkerCancel(warnInfo)
```

## updateWarnMarker

> <font color=#00aa00>在 v3.0 中已实现</font>

```javascript
/**
 * 更新报警点位位置
 * @param {Object} warnInfo : 点位信息,对象
 * 参数示例：

 */
  updateWarnMarker(warnInfo)
```
## demo

<head>
	<link href="../src/ol_v3.20.0/ol.css" rel="stylesheet" type="text/css" />
  <link href="../src/hdmap/hdmap.css" rel="stylesheet" type="text/css" />
	<script type="text/javascript" src="../src/ol_v3.20.0/ol-debug.js" charset="utf-8"></script>
  <script type="text/javascript" src="../src/hdmap/hdmap.js" charset="utf-8"></script>
  <link rel="stylesheet" href="https://unpkg.com/element-ui/lib/theme-chalk/index.css" type="text/css">
  <script type="text/javascript" src="https://unpkg.com/vue/dist/vue.js"></script>
  <script type="text/javascript" src="https://unpkg.com/element-ui/lib/index.js"></script>
  <script type="text/javascript" src="../src/jquery/jquery-3.2.1.js" charset="utf-8"></script>
</head>

<div>
  <div id="app">
    <div id="mapObj"></div>
    <div class="testbtn">
      <h4>报警点位操作</h4>
        <el-button type="primary" plain @click="warnStart(warnInfoA)">开启点位报警A</el-button>
        <el-button type="primary" plain @click="warnStart(warnInfoB)">开启点位报警B</el-button>
        <el-button type="primary" plain @click="warnCancel(warnInfoA)">解除点位报警A</el-button>
        <el-button type="primary" plain @click="warnCancel(warnInfoB)">解除点位报警B</el-button>
        <el-button type="primary" plain @click="warnUpdate(warnInfoC)">更新点位报警A</el-button>
        <el-button type="primary" plain @click="warnUpdate(warnInfoD)">更新点位报警B</el-button>
    </div>
  </div>
  <script>
    var app = new Vue({
      el: '#app',
      data: {
        // eslint-disable-next-line
        mapObj: null,
        warnInfoA: {
          id: '111',
          position: [6300, -4500],
          type: 'danger',
          text: '重点人员'
        },
        warnInfoB: {
          id: '222',
          position: [8600, -6400],
        },
        warnInfoC: {
          id: '111',
          position: [2700, -5200],
        },
        warnInfoD: {
          id: '222',
          position: [4300, -7000],
        }
      },
      mounted() {
        // 初始化地图
        this.mapObj = new hdmap.initMap({
          gisEngine: 'tile',
          sizeW: 13623,
          sizeH: 9796,
          domId: 'mapObj',
          mapUrl: 'http://zc200008pc1.hdsc.com/hdyj/',
          maxZoom: 6,
          minZoom: 0,
          zoom: 2,
          controlZoom: false,
          center: [0, 0],
          centerGPS: [113.619942, 23.304629],
          scale: 1.21,
          scaleType: 1,
          arcAngle: 1.2 // 弧度值
        })
        // 注册点击事件，监听鼠标点击点信息
        this.mapObj.regEventListener('singleclick', function (e) {
          console.log(e)
        })
      },
      methods: {
        // 开启点位报警
        warnStart (warnInfo) {
          this.mapObj.warnMarkerStart(warnInfo)
        },
        // 解除点位报警
        warnCancel (warnInfo) {
          this.mapObj.warnMarkerCancel(warnInfo)
        },
        // 更新点位报警
        warnUpdate (warnInfo) {
          this.mapObj.updateWarnMarker(warnInfo)
        }
      }
    })
  </script>
</div>

```html
<div>
  <div id="app">
    <div id="mapObj"></div>
    <div class="testbtn">
      <h4>报警点位操作</h4>
        <el-button type="primary" plain @click="warnStart(warnInfoA)">开启点位报警A</el-button>
        <el-button type="primary" plain @click="warnStart(warnInfoB)">开启点位报警B</el-button>
        <el-button type="primary" plain @click="warnCancel(warnInfoA)">解除点位报警A</el-button>
        <el-button type="primary" plain @click="warnCancel(warnInfoB)">解除点位报警B</el-button>
        <el-button type="primary" plain @click="warnUpdate(warnInfoC)">更新点位报警A</el-button>
        <el-button type="primary" plain @click="warnUpdate(warnInfoD)">更新点位报警B</el-button>
    </div>
  </div>
  <script>
    var app = new Vue({
      el: '#app',
      data: {
        // eslint-disable-next-line
        mapObj: null,
        warnInfoA: {
          id: '111',
          position: [6300, -4500],
          type: 'danger',
          text: '重点人员'
        },
        warnInfoB: {
          id: '222',
          position: [8600, -6400],
        },
        warnInfoC: {
          id: '111',
          position: [2700, -5200],
        },
        warnInfoD: {
          id: '222',
          position: [4300, -7000],
        }
      },
      mounted() {
        // 初始化地图
        this.mapObj = new hdmap.initMap({
          gisEngine: 'tile',
          sizeW: 13623,
          sizeH: 9796,
          domId: 'mapObj',
          mapUrl: 'http://zc200008pc1.hdsc.com/hdyj/',
          maxZoom: 6,
          minZoom: 0,
          zoom: 2,
          controlZoom: false,
          center: [0, 0],
          centerGPS: [113.619942, 23.304629],
          scale: 1.21,
          scaleType: 1,
          arcAngle: 1.2 // 弧度值
        })
        // 注册点击事件，监听鼠标点击点信息
        this.mapObj.regEventListener('singleclick', function (e) {
          console.log(e)
        })
      },
      methods: {
        // 开启点位报警
        warnStart (warnInfo) {
          this.mapObj.warnMarkerStart(warnInfo)
        },
        // 解除点位报警
        warnCancel (warnInfo) {
          this.mapObj.warnMarkerCancel(warnInfo)
        },
        // 更新点位报警
        warnUpdate (warnInfo) {
          this.mapObj.updateWarnMarker(warnInfo)
        }
      }
    })
  </script>
</div>
```
