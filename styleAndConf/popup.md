# 弹窗调用

## addPopup()

> <font color=#00aa00>在 v0.3.0 中已实现</font>

```javascript
/**
   * 创建弹窗
   * @param {Object || String} popOption 
   *  popOption: {
   *   domId: 'camera', 必填
   *   visible: true， 必填
   *   arrow: true 默认false，为true，不显示小箭头
   * } || popOption: 'camera'
   */
addPopup(popOption)
```

## showPopup()

> <font color=#00aa00>在 v0.3.0 中已实现</font>

```javascript
/**
   * 显示弹窗
   * @param {String} domId 弹窗id 必填
   * @param {Array} coordinate 位置
   * @param {Object} styleObj 自定义样式
   */
showPopup((domId, coordinate, styleObj)
```
## popupDefault()

> <font color=#00aa00>在 v0.3.0 中已实现</font>

```javascript
/**
   * 默认弹窗显示内容
   * @param {Array} coordinate click点的位置
   * @param {String} innerHTML 默认显示内容
   */
popupDefault((coordinate, innerHTML)
```

## popupMultipoint()

> <font color=#00aa00>在 v0.3.0 中已实现</font>

```javascript
/**
   * 点位聚合
   * @param {Array} coordinate  鼠标点击处的坐标信息
   * @param {Array} features    点位聚合列表
   */
popupMultipoint((coordinate, features)
```

## closePopup()

> <font color=#00aa00>在 v0.3.0 中已实现</font>

```javascript
/**
   * 关闭弹窗
   */
closePopup()
```

## closeCommonPopup()

> <font color=#00aa00>在 v0.3.0 中已实现</font>

```javascript
/**
   * 关闭普通弹窗（visible !== true）
   */
closeCommonPopup()
```

## closeSinglePopup()

> <font color=#00aa00>在 v1.1.0 中已实现</font>

```javascript
/**
   * 关闭某个弹窗（visible !== true）
   * @param {String} popName 弹窗节点名
   */
closeSinglePopup(popName)
```

## closeTypePopup()

> <font color=#00aa00>在 v1.1.0 中已实现</font>

```javascript
/**
   * 关闭某类弹窗
   * @param {String} type 类型
   */
closeTypePopup(type)
```

# 弹窗示例

```html
<!-- 弹窗调用步骤（前提：地图已初始化成功）： -->
  export default {
    data () {
      return {
        bitmap : null
      }
    },
    mounted: {
      <!-- 初始化方法详见方法 initMap() -->
      this.bitmap = new hdmap.initMap({
        gisEngine: 'bitmap',
        sizeW: 1920,
        sizeH: 1080,
        domId: 'mainMap',
        mapUrl: mainMapImg,
        maxZoom: 3,
        minZoom: 3,
        center: [112.334403, 39.8]
      })
    }
  }
  <!-- 自定义弹窗 -->
<!-- 1.html中写好弹窗，指定id -->
  <div id="broadcastPopup">样式、内容自定义</div>
<!-- 2.注册弹窗 (调用方法：addPopup(弹窗id) ) -->
  this.bitmap.addPopup('broadcastPopup')
<!-- 3.显示弹窗 （调用方法：showPopup（弹窗id, 显示位置（Array））） -->
  this.bitmap.showPopup('broadcastPopup', [20, 20])
<!-- 4.关闭弹窗 （调用方法：closePopup（）） -->
  this.bitmap.closePopup()
  <!-- 默认弹窗 -->
<!-- 调用方法：popupDefault（position（Array），innerHtml） -->
  this.bitmap.popupDefault([0,0], 'this is default popup')
<!-- 点位聚合 (调用方法：popupMultipoint(position（Array），features(Array)) ) -->
  this.bitmap.popupMultipoint([0,0], features)
```