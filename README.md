# Particle Cake

> 3D粒子蛋糕效果库 - 创建立体生日蛋糕动画

[English](./README.md) | [中文](./README_zh.md)

## 特性

- 精美的3D粒子蛋糕效果
- 点击触发烟花爆炸动画
- 烟花散开后自动形成文字
- 响应式设计，自动适配移动端
- 只需导入即可使用，内置各种参数

## 安装

### 方式一：CDN 引入（推荐）

```html
<!-- 引入 Three.js -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<!-- 引入 Particle Cake -->
<script src="https://unpkg.com/particle-cake/dist/particle-cake.min.js"></script>
```

或使用 jsDelivr:

```html
<script src="https://cdn.jsdelivr.net/npm/particle-cake/dist/particle-cake.min.js"></script>
```

### 方式二：npm 安装

```bash
npm install particle-cake
```

```javascript
// ES6 模块
import ParticleCake from 'particle-cake';
// 需要自行引入 Three.js
import * as THREE from 'three';
```

## 快速开始

### 基础用法

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Birthday Page</title>
    <style>
        body {
            margin: 0;
            background: linear-gradient(160deg, #050510 0%, #0b1230 52%, #1c2c5b 100%);
        }
        #canvas-box {
            width: 100vw;
            height: 100vh;
        }
    </style>
</head>
<body>
    <div id="canvas-box"></div>
    
    <!-- 引入 Three.js -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <!-- 引入 Particle Cake -->
    <script src="https://unpkg.com/particle-cake/dist/particle-cake.min.js"></script>
    
    <script>
        // 创建粒子蛋糕实例
        const cake = new ParticleCake('canvas-box', {
            text: '生日快乐!',
            particleCount: 15000
        });

        // 点击触发烟花爆炸
        document.body.addEventListener('click', () => {
            cake.explode();
        });
    </script>
</body>
</html>
```

## 配置选项

| 参数 | 类型 | 默认值 | 说明 |
|------|------|--------|------|
| `text` | string | `'生日快乐'` | 显示的文字 |
| `particleCount` | number | `15000` | 粒子数量（移动端自动减少） |
| `particleSize` | number | `3` | 粒子大小 |
| `textSize` | number | `150` | 文字大小 |
| `fontFamily` | string | `'Microsoft YaHei'` | 字体 |
| `candleColor` | string | `'#FFFF00'` | 蜡烛颜色 |
| `cameraZ` | number | `400` | 相机距离 |
| `textScale` | number | `1.2` | 文字缩放比例 |

## 示例

### 基础示例

```javascript
const cake = new ParticleCake('container');
```

### 自定义文字

```javascript
const cake = new ParticleCake('container', {
    text: 'Happy Birthday!',
    textSize: 120,
    candleColor: '#FF6B6B'
});
```

### 触发烟花效果

```javascript
const cake = new ParticleCake('container');

// 点击页面任意位置触发烟花
document.body.addEventListener('click', () => {
    cake.explode();
});
```

## 效果展示

1. **初始状态**: 3D粒子组成的蛋糕形态，蜡烛顶部有闪烁的火苗
2. **点击后**: 粒子爆炸成烟花效果
3. **2秒后**: 烟花粒子聚合成预设的文字

## 方法

### `explode()`

触发烟花爆炸效果，将蛋糕粒子散开成彩色烟花。

### `destroy()`

销毁实例，释放所有资源。

```javascript
const cake = new ParticleCake('container');
// 销毁实例
cake.destroy();
```

## 响应式

库会自动检测屏幕宽度，在移动端（宽度 < 768px）会自动：
- 减少粒子数量到 5000
- 减小粒子大小到 1.2
- 减小文字大小到 35
- 调整相机位置

## 开发

```bash
# 克隆仓库
git clone https://github.com/VignaChu/particle-cake.git
cd particle-cake

# 安装依赖
npm install

# 查看示例
npm run demo
```

## 许可证

MIT License - 详见 [LICENSE](LICENSE) 文件

## 致谢

- [Three.js](https://threejs.org/) - 3D 渲染库
