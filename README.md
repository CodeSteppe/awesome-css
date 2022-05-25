# 冷门又好用的 CSS 特性

## 1. 多列布局（Multi-column Layout）

> [MDN - CSS Multi-column Layout](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Columns)

> [Can I Use - CSS3 Multi-column Layout](https://caniuse.com/multicolumn)

CSS 提供了对多列布局的支持。支持设置布局中的列数 (`column-count`)、内容应如何列之间的流动规则、列之间的间距 (`column-gap`) 以及列分割线（`column-rule`）的样式。

比如可以实现下面的瀑布流效果：

![mansonry](./images/multi-column.png)

[**Codepen demo**](https://codepen.io/mudontire/pen/yLevxRr)

**主要样式：**

```scss
.masonry {
  width: 1440px;
  margin: 20px auto;
  columns: 4;
  column-gap: 30px;

  .item {
    width: 100%;
    break-inside: avoid;
    margin-bottom: 30px;

    img {
      width: 100%;
    }
  }
}
```

# 2. 书写模式（Writing Modes）

> [MDN - CSS Writing Modes](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Writing_Modes)

> [Can I Use - CSS writing-mode property](https://caniuse.com/css-writing-mode)

Writing Modes 定义了各种国际书写模式，例如从左到右（拉丁语、印度语）、从右到左（希伯来语、阿拉伯语）、双向（混合从左到右和从右到左的语言）和垂直（汉语）。

下面是三种书写方式的展示：

![writingModes](./images/writing_modes.png)

[**Codepen demo**](https://codepen.io/mudontire/pen/Yzreqvx)

**关键样式:**

```scss
.left-to-right {
  direction: ltr;
}

.right-to-left {
  direction: rtl;
}

.vertical {
  writing-mode: vertical-rl;
}
```

或者，可以用来实现一个黑客帝国的 code rain：

[**Codepen - Matrix code rain**](https://codepen.io/mudontire/pen/YzreyWL)

# 3. `aspect-ratio` 属性

> [MDN - aspect-ratio](https://developer.mozilla.org/en-US/docs/Web/CSS/aspect-ratio)

> [Can I Use - CSS property: aspect-ratio](https://caniuse.com/mdn-css_properties_aspect-ratio)

CSS 的 `aspect-ratio` 属性用于设置元素的首选宽高比，可以自动计算宽度、高度和其他一些布局功能，省去同时计算宽和高的工作。

比如，视频网站可以设置视频播放窗口比例为 16/9：

![aspect-ratio](./images/aspect-ratio.png)

[Codepen demo](https://codepen.io/mudontire/pen/mdBXPqB)

**关键样式：**

```scss
.video-box {
  width: 70vw;
  background-color: #000;
  aspect-ratio: 16/9;
}
```

# 4. `gap` 属性

> [MDN - gap](https://developer.mozilla.org/en-US/docs/Web/CSS/gap)

> [Can I Use - gap property for Flexbox](https://caniuse.com/flexbox-gap)

CSS 的 `gap` 属性用于 flex 和 grid 布局时设置行和列之间的间隔，是 `row-gap` 和 `column-gap` 的简写。

以前在使用 flex 布局的时候经常会用 `margin`、`padding` 来控制 flex item 之间的间隔，用 `gap` 会更方便。

比如:

```html
<div class="flex-box">
  <div class="item"></div>
  <div class="item"></div>
  <div class="item"></div>
  <div class="item"></div>
  <div class="item"></div>
  <div class="item"></div>
  <div class="item"></div>
  <div class="item"></div>
  <div class="item"></div>
</div>
```

```scss
.flex-box {
  display: flex;
  width: 400px;
  flex-wrap: wrap;
  gap: 20px;
}

.item {
  width: 120px;
  height: 60px;
  background-color: c·rimson;
}
```

![gap](./images/gap.png)

[**Codepen demo**](https://codepen.io/mudontire/pen/ExwQKGK)

# 5. CSS Shapes

> [MDN - CSS Shapes](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Shapes)

> [Can I Use - CSS Shapes Level 1](https://caniuse.com/css-shapes)

CSS Shapes 用于描述元素的几何形状。元素的常规形状就是矩形，使用 CSS Shapes 可以将元素定义为圆、椭圆或多边形。

对于 Level 1 规范，CSS Shapes 可以应用于浮动元素。 该规范定义了不同的方法来定义浮动元素上的形状。

比如，实现下面文字环绕圆形图片的效果：

![shapes](./images/shapes.png)

[**Codepen demo**](https://codepen.io/mudontire/pen/eYGVzdz)

**关键样式：**

```scss
img {
  width: 300px;
  float: left;
  shape-outside: circle(50%);
}
```

# 6. `object-fit` 属性

> [MDN - object-fit](https://developer.mozilla.org/en-US/docs/Web/CSS/object-fit)

> [Can I Use - CSS3 object-fit/object-position](https://caniuse.com/object-fit)

`object-fit` 属性用于设置 [replaced element](https://developer.mozilla.org/en-US/docs/Web/CSS/Replaced_element)（例如 `<img>` 或 `<video>`）的内容如何适配其容器的尺寸。

比如，调整一张图片在容器里面的显示：

![object-fit](./images/object-fit.png)

[**Codepen demo**](https://codepen.io/mudontire/pen/BawYJrQ)

# 7. `filter` 属性

> [MDN - filter](https://developer.mozilla.org/en-US/docs/Web/CSS/filter)

> [Can I Use - CSS Filter Effects](https://caniuse.com/css-filters)

CSS 的 `filter` 属性将图像的效果调整（模糊、对比度、灰度、色调等）应用于元素。`filter` 通常用于调整图像、背景和边框的渲染。

比如，每年的国家公祭日很多网站会把颜色调整成黑白，就可以用 `filter` 一行代码搞定：

![gray-scale](./images/gray-scale.png)

# 8. `backdrop-filter` 属性

与 `filter` 类似的属性，`backdrop-filter` 属性将图形效果（例如模糊或颜色偏移）应用于元素的背景区域。 因为它适用于元素后面的所有内容，使用时需要将元素或其背景至少部分设置为透明才能看到效果。

> [MDN - backdrop-filter](https://developer.mozilla.org/en-US/docs/Web/CSS/backdrop-filter)

> [Can I Use - CSS Backdrop Filter](https://caniuse.com/css-backdrop-filter)

比如，可以用它做一个毛玻璃的效果：

![backdrop-filter](./images/backdrop-filter.png)

[**Codepen demo**](https://codepen.io/mudontire/pen/dyVdqow)

**关键代码：**

```html
<div class="box">
  <p>
    If I know what love is
    <br />it is because of you
  </p>
</div>
```

```scss
.box {
  background: url(../images/roses.jpg) no-repeat;
}

p {
  background-color: rgba(255, 255, 255, 0.3);
  backdrop-filter: blur(20px);
  color: white;
}
```

# 9. `conic-gradient()` 函数

> [MDN - conic-gradient()](<https://developer.mozilla.org/en-US/docs/Web/CSS/gradient/conic-gradient()>)

> [Can I Use - conic-gradient()](https://caniuse.com/mdn-css_types_image_gradient_conic-gradient)

CSS 中的 `linear-gradient()` 函数大家应该接触的不少，除此之外 gradient 家族中还有 `radial-gradient()`、`conic-gradient()` 等，更多类型可参考 [MDN - gradient](https://developer.mozilla.org/en-US/docs/Web/CSS/gradient)。

`conic-gradient()` 函数创建一个图像，该图像由渐变色组成，颜色围绕中心点旋转过渡（而不是从中心辐射）。

例如，常见的渐变色仪表盘图表就可以用 `conic-gradient()` 函数绘制：

![gauge](./images/gauge.png)

[**Codepen demo**](https://codepen.io/mudontire/pen/LYzQJLq)

# 10. `accent-color` 属性

> [MDN - accent-color](https://developer.mozilla.org/en-US/docs/Web/CSS/accent-color)

> [Can I Use - CSS property: accent-color](https://caniuse.com/mdn-css_properties_accent-color)

CSS 的 `accent-color` 属性用于设置由某些元素生成的 UI 控件的强调色。比如 `<input>` 元素生成的 `checkbox` 和 `radio` 控件被选中时的颜色。

比如，改变以下元素的强调色：

![accent-color](./images/accent-color.png)

[**Codepen demo**](https://codepen.io/mudontire/pen/XWeZLLa)

**关键代码：**

```html
<input type="checkbox" class="checkbox" checked />
<input type="radio" class="radio" checked />
<input type="range" class="range" />
<progress value="70" max="100" class="progress">70%</progress>
```

```scss
.checkbox {
  width: 40px;
  height: 40px;
  accent-color: crimson;
}

.radio {
  width: 40px;
  height: 40px;
  accent-color: dodgerblue;
}

.range {
  width: 200px;
  accent-color: lawngreen;
}

.progress {
  width: 200px;
  accent-color: coral;
}
```

# 11. 滚动捕捉（Scroll Snap）

> [MDN - CSS Scroll Snap](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Scroll_Snap)

> [Can I Use - CSS Scroll Snap](https://caniuse.com/css-snappoints)

CSS Scroll Snap 引入了对滚动位置的捕捉，它强制执行滚动操作完成后滚动容器的滚动端口可能结束的位置。

比如，我想让每次滚动结束的位置都停在下一个元素开头，实现一个滚动翻页的效果：

![scroll-snap](./images/scroll-snap.gif)

[**Codepen demo**](https://codepen.io/mudontire/pen/dyVdxvr)

**关键代码：**

```html
<article class="scroller">
  <section>
    <h2>Page one</h2>
  </section>
  <section>
    <h2>Page two</h2>
  </section>
  <section>
    <h2>Page three</h2>
  </section>
  <section>
    <h2>Page four</h2>
  </section>
</article>
```

```scss
.scroller {
  overflow-y: scroll;
  scroll-snap-type: y mandatory;
}

section {
  scroll-snap-align: start;
}
```

# 12. `overscroll-behavior` 属性

> [MDN - overscroll-behavior](https://developer.mozilla.org/en-US/docs/Web/CSS/overscroll-behavior)

> [Can I Use - CSS overscroll-behavior](https://caniuse.com/css-overscroll-behavior)

CSS的 `overscroll-behavior` 属性用于定义元素滚动到滚动区域边界时的行为。 它是 [overscroll-behavior-x](https://developer.mozilla.org/en-US/docs/Web/CSS/overscroll-behavior-x) 和 [overscroll-behavior-y](https://developer.mozilla.org/en-US/docs/Web/CSS/overscroll-behavior-y) 的简写。

浏览器的默认行为是：当子元素滚动到边界后继续滚动鼠标，会触发父元素的滚动。该行为被称作 **scroll chaining**。很多时候我们不需要这样的行为，比如当我们滚动一个弹窗中的内容时，不希望后面的页面也跟着滚动。通过设置 `overscroll-behavior:contain` 就可以修改这一行为，而不需要监听 `scroll` 事件去阻止冒泡。

**示例**：[Codepen demo](https://codepen.io/mudontire/pen/ExwQqdO)

# 

好了，目前能想到的就是这么多，希望对大家更高效、更优雅的画页面有帮助 😀！
