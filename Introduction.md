# 简介

地图引擎hdmap是使用openlayers 4.5.0版本封装出的一套js类库，暴露了一系列web API供恒大智慧小区项目使用。

应用可以通过地图引擎API处理GIS地图和光栅图，以及符合WMS规范的切片地图加载，可以实现地图的显示和缩放移动等地图操作。应用也可以在地图上实现点位管理、路线绘制和区域描边等功能，以实现各个小区管理、停车场、门禁、巡更等场景的业务需求。

地图引擎会在系统应用的主框架处引入。在引入地图引擎后，会在全局对象上存在一个hdmap对象，在hdmap上包含了地图的初始化函数initMap，地图管理器mapManager，地图默认样式集mapCommonConfig，地图工具函数集utils等属性。

# 引入使用

首先需要在工程的package.json中的依赖处引入

```javascript
  "dependencies": {
    ···
    // 依赖v1.*.*版本时使用此分支
    "hdmap": "git+http://gitlab/xiaxuanyin/UI-mapcomponent.git#master",
    // 依赖v2.*.*版本时使用此分支
    "hdmap": "git+http://gitlab/xiaxuanyin/UI-mapcomponent.git#buildv2",
    // 依赖v3.*.*版本时使用此分支
    "hdmap": "git+http://gitlab/xiaxuanyin/UI-mapcomponent.git#buildv3"
    ···
  },
```

然后通过npm安装依赖

其次要在工程入口文件处引入hdmap和css文件

```javascript
import 'hdmap'
import 'hdmap/dist/hdmap.css'
```

及存在全局的hdmap对象，使用方法请看[初始化](map/init.md)

# 版本控制及更新

当我们发布版本时，开发使用者只需要在项目中运行
```javascript
npm update
```
即可更新hdmap版本。如有问题需要制定版本时，请将依赖中的master改为指定版本即可。

我们的版本更新会在开发群同步给大家，如有问题，可以到[仓库问题](http://gitlab/xiaxuanyin/UI-mapcomponent/issues)处反馈，或者按照接下来项目问题管理的流程提出。


# branches 分支说明
### master
作为dev2分支的版本发布分支，为POC3分支的代码支撑

版本号： 1.\*.\*
### buildv2
作为dev分支的版本发布分支，为POC4以后的业务进行支撑

版本号：2.\*.\*
### buildv3
作为dev_v3分支的版本发布分支，为新大屏以后的业务进行支撑

版本号：3.\*.\*
### dev
比例尺、旋转角、中心GPS、GPS映射算法更新后开发分支，新代码发布在buildv2分支
### dev2
默认所上传的地图的坐标系为上北下南方向，选点计算比例尺、中心GPS和GPS映射算法

不考虑地图旋转，新代码发布在master分支上

已锁定版本，无重大bug不进行更新

### dev_v3
支持切片地图加载和计算的3.*版本的开发分支
### myopenlayers
openlayers源码分支，被hdmap仓库依赖，在工程中提供ol源码
### mapbook
hdmap API网站源码分支，构建markdown语法的地图引擎API
