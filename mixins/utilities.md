## Utilities类  
utilities是一个工具类，里面包含了一些我们常用的类。  

## 正文开始部分
 * <a href="#hide-text">隐藏块中的文字</a>
   * .hide-text();
   * .text-hide();

 * <a href="#opacity">带透明(滤镜)效果</a>
  * .opacity(@opacity);//合法值:0-1

 * <a href="#image">横向响应式</a>
  * .img-responsive(@display: block);

 * <a href="#image">retina图片类,retina频幕优化(使用方式待补充)</a>
  * .img-retina(@file-1x; @file-2x; @width-1x; @height-1x)；

 * <a href="#labels">背景色置为@color;若带有href属性对象,在hover与focus,背景色draken 10%(优先级:.a+[]+:)</a>
  * .label-variant(@color);//适合背景会变化的a标签
 
 * <a href="#reset-filter">当要移除gradient的时候，需要用这个类reset</a>
  * .reset-filter();

 * <a href="#resize">让块元素可以调整大小(注意兼容性)</a>
  * .resizable(@dir);//可用值:horizontal,vertical,both
  
 * <a href="#responsive-visibility">元素自适应</a>
  * .responsive-visibility();//让元素可以自适应(包括table及其子元素)
  * .responsive-invisibility();//令元素消失

 * <a href="#size">对于块元素的大小进行控制</a>
  * .size(@width; @height);//规定元素的大小
  * .square(@size);//正方形控制

 * <a href="#tab-focus">tab键选择中时的外观,外面出现dotted线</a>
  * .tab-focus();

 * <a href="#text-emphasis">颜色置为@color;若元素为a元素,则在hover时候颜色darken 10%.(优先级:a+.a+:)</a>
  * .text-emphasis-variant(@color);

 * <a href="#text-overflow">规定大小的block与inline-block溢出部分出现省略号</a>
  * .text-overflow();

 * <a href="#vendor-prefixed">浏览器兼容性前缀,在v4中将会由autoprefix取代</a>
  * <a href="#Animation">Animation</a>
    * .animation(@animation);
    * .animation-name(@name);
    * .animation-duration(@duration);
    * .animation-timing-function(@timing-function);
    * .animation-delay(@delay);
    * .animation-iteration-count(@iteration-count);
    * .animation-direction(@direction);
    * .animation-fill-mode(@fill-mode);
  * <a href="#Transform">Transform</a>
    * .scale(@ratio);
    * .scale(@ratioX; @ratioY);
    * .scaleX(@ratio);
    * .scaleY(@ratio);
    * .skew(@x; @y);
    * .translate(@x; @y);
    * .translate3d(@x; @y; @z);
    * .rotate(@degrees);
    * .rotateX(@degrees);
    * .rotateY(@degrees);
    * .perspective(@perspective);
    * .perspective-origin(@perspective);  
    * .transform-origin(@origin); 
  * <a href="#Transition">Transition</a>
    * .transition(@transition);  
    * .transition-property(@transition-property);  
    * .transition-delay(@transition-delay);  
    * .transition-duration(@transition-duration);  
    * .transition-timing-function(@timing-function);  
    * .transition-transform(@transition);
  * <a href="#Backface-visibility">Backface visibility</a>
    * .backface-visibility(@visibility)//for 3d
  * <a href="#Box-shadows">Box shadows</a>
    * .box-shadow(@shadow);
  * <a href="#Box-sizing">Box sizing</a>
    * .box-sizing(@boxmodel);
  * <a href="#CSS3-Content-Columns">CSS3 Content Columns</a>
    * .content-columns(@column-count; @column-gap: **@grid-gutter-width**);
  * <a href="#Optional-hyphenation">Optional hyphenation</a>
    * .hyphens(@mode: auto);
  * <a href="#Placeholder-text">Placeholder text</a>
    * .placeholder(@color: **@input-color-placeholder**);//优先级()
  * <a href="#User-select">User select</a>
    * .user-select(@select);

## 代码部分
<a id="hide-text"></a>
### 位置:hide-text.less
````html
.hide-text() {
  font: ~"0/0" a;
  color: transparent;
  text-shadow: none;
  background-color: transparent;
  border: 0;
}
.text-hide() {
  .hide-text();
}
````
<a id="opacity"></a>
### 位置:opacity.less
````html
.opacity(@opacity) {
  opacity: @opacity;
  @opacity-ie: (@opacity * 100);// IE8 filter
  filter: ~"alpha(opacity=@{opacity-ie})";
}
````
<a id="image"></a>
### 位置:image.less
````html
.img-responsive(@display: block) {
  display: @display;
  max-width: 100%; // Part 1: Set a maximum relative to the parent
  height: auto; // Part 2: Scale the height according to the width, otherwise you get stretching
}
.img-retina(@file-1x; @file-2x; @width-1x; @height-1x) {
  background-image: url("@{file-1x}");
  @media
  only screen and (-webkit-min-device-pixel-ratio: 2),
  only screen and (   min--moz-device-pixel-ratio: 2),
  only screen and (     -o-min-device-pixel-ratio: 2/1),
  only screen and (        min-device-pixel-ratio: 2),
  only screen and (                min-resolution: 192dpi),
  only screen and (                min-resolution: 2dppx) {
    background-image: url("@{file-2x}");
    background-size: @width-1x @height-1x;
  }
}
````
<a id="labels"></a>
### 位置:labels.less
````html
.label-variant(@color) {
  background-color: @color;
  &[href] {
    &:hover,
    &:focus {
      background-color: darken(@color, 10%);//优先级0010+0010+0010
    }
  }
}
````
<a id="reset-filter"></a>
### 位置:reset-filter.less
````html
.reset-filter() {
  filter: e(%("progid:DXImageTransform.Microsoft.gradient(enabled = false)"));
}
````
<a id="resize"></a>
### 位置:resize.less
````html
.resizable(@direction) {
  resize: @direction; // Options: horizontal, vertical, both
  overflow: auto; // Per CSS3 UI, `resize` only applies when `overflow` isn't `visible`
}
````
<a id="responsive-visibility"></a>
### 位置:responsive-visibility.less
````html
.responsive-visibility() {
  display: block !important;
  table&  { display: table; }
  tr&     { display: table-row !important; }
  th&,
  td&     { display: table-cell !important; }
}

.responsive-invisibility() {
  display: none !important;
}
````
<a id="size"></a>
### 位置:size.less
````html
.size(@width; @height) {
  width: @width;
  height: @height;
}

.square(@size) {
  .size(@size; @size);
}
````
<a id="tab-focus"></a>
### 位置:tab-focus.less
````html
.tab-focus() {
  // Default
  outline: thin dotted;
  // WebKit
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
````
<a id="text-emphasis"></a>
### 位置:text-emphasis.less
````html
.text-emphasis-variant(@color) {
  color: @color;
  a&:hover {
    color: darken(@color, 10%);
  }
}
````
<a id="text-overflow"></a>
### 位置:text-overflow.less
````html
.text-overflow() {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
````
<a id="vendor-prefixes"></a>
### 位置:vendor-prefixes.less
<a id="Animation"></a>
````html
// Animations
.animation(@animation) {
  -webkit-animation: @animation;
       -o-animation: @animation;
          animation: @animation;
}
.animation-name(@name) {
  -webkit-animation-name: @name;
          animation-name: @name;
}
.animation-duration(@duration) {
  -webkit-animation-duration: @duration;
          animation-duration: @duration;
}
.animation-timing-function(@timing-function) {
  -webkit-animation-timing-function: @timing-function;
          animation-timing-function: @timing-function;
}
.animation-delay(@delay) {
  -webkit-animation-delay: @delay;
          animation-delay: @delay;
}
.animation-iteration-count(@iteration-count) {
  -webkit-animation-iteration-count: @iteration-count;
          animation-iteration-count: @iteration-count;
}
.animation-direction(@direction) {
  -webkit-animation-direction: @direction;
          animation-direction: @direction;
}
.animation-fill-mode(@fill-mode) {
  -webkit-animation-fill-mode: @fill-mode;
          animation-fill-mode: @fill-mode;
}
````
<a id="Transform"></a>
````html
// Transformations
.scale(@ratio) {
  -webkit-transform: scale(@ratio);
      -ms-transform: scale(@ratio); // IE9 only
       -o-transform: scale(@ratio);
          transform: scale(@ratio);
}
.scale(@ratioX; @ratioY) {
  -webkit-transform: scale(@ratioX, @ratioY);
      -ms-transform: scale(@ratioX, @ratioY); // IE9 only
       -o-transform: scale(@ratioX, @ratioY);
          transform: scale(@ratioX, @ratioY);
}
.scaleX(@ratio) {
  -webkit-transform: scaleX(@ratio);
      -ms-transform: scaleX(@ratio); // IE9 only
       -o-transform: scaleX(@ratio);
          transform: scaleX(@ratio);
}
.scaleY(@ratio) {
  -webkit-transform: scaleY(@ratio);
      -ms-transform: scaleY(@ratio); // IE9 only
       -o-transform: scaleY(@ratio);
          transform: scaleY(@ratio);
}
.skew(@x; @y) {
  -webkit-transform: skewX(@x) skewY(@y);
      -ms-transform: skewX(@x) skewY(@y); // See https://github.com/twbs/bootstrap/issues/4885; IE9+
       -o-transform: skewX(@x) skewY(@y);
          transform: skewX(@x) skewY(@y);
}
.translate(@x; @y) {
  -webkit-transform: translate(@x, @y);
      -ms-transform: translate(@x, @y); // IE9 only
       -o-transform: translate(@x, @y);
          transform: translate(@x, @y);
}
.translate3d(@x; @y; @z) {
  -webkit-transform: translate3d(@x, @y, @z);
          transform: translate3d(@x, @y, @z);
}
.rotate(@degrees) {
  -webkit-transform: rotate(@degrees);
      -ms-transform: rotate(@degrees); // IE9 only
       -o-transform: rotate(@degrees);
          transform: rotate(@degrees);
}
.rotateX(@degrees) {
  -webkit-transform: rotateX(@degrees);
      -ms-transform: rotateX(@degrees); // IE9 only
       -o-transform: rotateX(@degrees);
          transform: rotateX(@degrees);
}
.rotateY(@degrees) {
  -webkit-transform: rotateY(@degrees);
      -ms-transform: rotateY(@degrees); // IE9 only
       -o-transform: rotateY(@degrees);
          transform: rotateY(@degrees);
}
.perspective(@perspective) {
  -webkit-perspective: @perspective;
     -moz-perspective: @perspective;
          perspective: @perspective;
}
.perspective-origin(@perspective) {
  -webkit-perspective-origin: @perspective;
     -moz-perspective-origin: @perspective;
          perspective-origin: @perspective;
}
.transform-origin(@origin) {
  -webkit-transform-origin: @origin;
     -moz-transform-origin: @origin;
      -ms-transform-origin: @origin; // IE9 only
          transform-origin: @origin;
}
````
<a id="Transition"></a>
````html
// Transitions
.transition(@transition) {
  -webkit-transition: @transition;
       -o-transition: @transition;
          transition: @transition;
}
.transition-property(@transition-property) {
  -webkit-transition-property: @transition-property;
          transition-property: @transition-property;
}
.transition-delay(@transition-delay) {
  -webkit-transition-delay: @transition-delay;
          transition-delay: @transition-delay;
}
.transition-duration(@transition-duration) {
  -webkit-transition-duration: @transition-duration;
          transition-duration: @transition-duration;
}
.transition-timing-function(@timing-function) {
  -webkit-transition-timing-function: @timing-function;
          transition-timing-function: @timing-function;
}
.transition-transform(@transition) {
  -webkit-transition: -webkit-transform @transition;
     -moz-transition: -moz-transform @transition;
       -o-transition: -o-transform @transition;
          transition: transform @transition;
}
````
<a id="Backface-visibility"></a>
````html
// Backface visibility
.backface-visibility(@visibility){
  -webkit-backface-visibility: @visibility;
     -moz-backface-visibility: @visibility;
          backface-visibility: @visibility;
}
````
<a id="Box-shadow"></a>
````html
//Box shadow
.box-shadow(@shadow) {
  -webkit-box-shadow: @shadow; // iOS <4.3 & Android <4.1
          box-shadow: @shadow;
}
````
<a id="Box-sizing"></a>
````html
// Box sizing
.box-sizing(@boxmodel) {
  -webkit-box-sizing: @boxmodel;
     -moz-box-sizing: @boxmodel;
          box-sizing: @boxmodel;
}
````
<a id="CSS3-Content-Columns"></a>
````html
// CSS3 Content Columns
.content-columns(@column-count; @column-gap: @grid-gutter-width) {
  -webkit-column-count: @column-count;
     -moz-column-count: @column-count;
          column-count: @column-count;
  -webkit-column-gap: @column-gap;
     -moz-column-gap: @column-gap;
          column-gap: @column-gap;
}
````
<a id="Optional-hyphenation"></a>
````html
// Optional hyphenation
.hyphens(@mode: auto) {
  word-wrap: break-word;
  -webkit-hyphens: @mode;
     -moz-hyphens: @mode;
      -ms-hyphens: @mode; // IE10+
       -o-hyphens: @mode;
          hyphens: @mode;
}
````
<a id="Placeholder-text"></a>
````html
// Placeholder text
.placeholder(@color: @input-color-placeholder) {
  // Firefox
  &::-moz-placeholder {
    color: @color;
    opacity: 1; // See https://github.com/twbs/bootstrap/pull/11526
  }
  &:-ms-input-placeholder { color: @color; } // Internet Explorer 10+
  &::-webkit-input-placeholder  { color: @color; } // Safari and Chrome
}
````
<a id="User-select"></a>
````html
// User select
// For selecting text on the page
.user-select(@select) {
  -webkit-user-select: @select;
     -moz-user-select: @select;
      -ms-user-select: @select; // IE10+
          user-select: @select;
}
````







