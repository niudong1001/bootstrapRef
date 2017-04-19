## Components类
components类是一个基本的组建类，里面包含了我们常用的组件。  

## 正文开始部分

* <a href="#alert-variant">警告块变量</a>
 * .alert-variant(@bg-color; @border-color; @text-color);
   * hr;//border-color darken 5%
   * .alert-link;// color darken 10%

* <a href="#button-variant">按钮变量</a>
 * .button-variant(@color; @background; @border);//全为color
   * .badge;//小图标
 * .button-size(@padding-vertical; @padding-horizontal; @font-size; @line-height; @border-radius);

* <a href="#panel-variant">面板变量</a>
 * .panel-variant(@border; @heading-text-color; @heading-bg-color; @heading-border);//all color
   * .panel-heading;
     * .badge;
      * .panel-collapse;
        * .panel-body;
    * .panel-footer;
      * .panel-collapse;
        * .panel-body;

* <a href="#pagination-size">页码pagination(翻页控件使用)</a> 
 * .pagination-size(@padding-vertical; @padding-horizontal; @font-size; @border-radius)
    * a;
    * span;

* <a href="#list-group-item-variant">列表项变量</a>
 * .list-group-item-variant(@state; @background; @color);
   * &a;
     * .list-group-item-heading;

* <a href="#nav-divider">nav分隔符</a>
 * .nav-divider(@color: #e5e5e5);//**@line-height-computed**

* <a href="#forms">表单控制部分</a>
  * .form-control-validation(@text-color: #555; @border-color: #ccc; @background-color: #f5f5f5)
    * .help-block,
    * .control-label,
    * .radio,
    * .checkbox,
    * .radio-inline,
    * .checkbox-inline
    * .form-control
    * .input-group-addon
    * .form-control-feedback
  * .form-control-focus(@color: @input-border-focus)
  * .input-size(@input-height; @padding-vertical; @padding-horizontal; @font-size; @line-height; @border-radius)
    * select&
    * textarea&,select[multiple]&

* <a href="#progress-bar">进度条</a>
  * .progress-bar-variant(@color)
    * .progress-striped &

* <a href="#table-row">表格行的背景与hover控制</a>
  * .table-row-variant(@state; @background)
    * table-hover

## 代码部分
<a id="alert-variant"></a>
### 位置alerts.less
````html
.alert-variant(@background; @border; @text-color) {
  background-color: @background;
  border-color: @border;
  color: @text-color;

  hr {
    border-top-color: darken(@border, 5%);
  }
  .alert-link {
    color: darken(@text-color, 10%);
  }
}
````
<a id="button-variant"></a>
### 位置buttons.less
````html
.button-variant(@color; @background; @border) {
  color: @color;
  background-color: @background;
  border-color: @border;

  &:hover,
  &:focus,
  &.focus,
  &:active,
  &.active,
  .open > .dropdown-toggle& {
    color: @color;
    background-color: darken(@background, 10%);
        border-color: darken(@border, 12%);
  }
  &:active,
  &.active,
  .open > .dropdown-toggle& {
    background-image: none;
  }
  &.disabled,
  &[disabled],
  fieldset[disabled] & {
    &,
    &:hover,
    &:focus,
    &.focus,
    &:active,
    &.active {
      background-color: @background;
          border-color: @border;
    }
  }

  .badge {
    color: @background;
    background-color: @color;
  }
}
// Button sizes
.button-size(@padding-vertical; @padding-horizontal; @font-size; @line-height; @border-radius) {
  padding: @padding-vertical @padding-horizontal;
  font-size: @font-size;
  line-height: @line-height;
  border-radius: @border-radius;
}
````
<a id="panel-variant"></a>
### 位置panels.less
````html
.panel-variant(@border; @heading-text-color; @heading-bg-color; @heading-border) {
  border-color: @border;

  & > .panel-heading {
    color: @heading-text-color;
    background-color: @heading-bg-color;
    border-color: @heading-border;

    + .panel-collapse > .panel-body {
      border-top-color: @border;
    }
    .badge {
      color: @heading-bg-color;
      background-color: @heading-text-color;
    }
  }
  & > .panel-footer {
    + .panel-collapse > .panel-body {
      border-bottom-color: @border;
    }
  }
}
````
<a id="pagination-size"></a>
### 位置pagination.less
````html
.pagination-size(@padding-vertical; @padding-horizontal; @font-size; @border-radius) {
  > li {
    > a,
    > span {
      padding: @padding-vertical @padding-horizontal;
      font-size: @font-size;
    }
    &:first-child {
      > a,
      > span {
        .border-left-radius(@border-radius);
      }
    }
    &:last-child {
      > a,
      > span {
        .border-right-radius(@border-radius);
      }
    }
  }
}

````
<a id="list-group-item-variant"></a>
### 位置list-group.less
````html
.list-group-item-variant(@state; @background; @color) {
  .list-group-item-@{state} {
    color: @color;
    background-color: @background;

    a& {
      color: @color;

      .list-group-item-heading {
        color: inherit;
      }

      &:hover,
      &:focus {
        color: @color;
        background-color: darken(@background, 5%);
      }
      &.active,
      &.active:hover,
      &.active:focus {
        color: #fff;
        background-color: @color;
        border-color: @color;
      }
    }
  }
}
````
<a id="nav-divider"></a>
### 位置nav-divider.less
````html
.nav-divider(@color: #e5e5e5) {
  height: 1px;
  margin: ((@line-height-computed / 2) - 1) 0;
  overflow: hidden;
  background-color: @color;
}
````
<a id="forms"></a>
### 位置forms.less
````html
// Used in forms.less to generate the form validation CSS for warnings, errors,
// and successes.

.form-control-validation(@text-color: #555; @border-color: #ccc; @background-color: #f5f5f5) {
  // Color the label and help text
  .help-block,
  .control-label,
  .radio,
  .checkbox,
  .radio-inline,
  .checkbox-inline,
  &.radio label,
  &.checkbox label,
  &.radio-inline label,
  &.checkbox-inline label  {
    color: @text-color;
  }
  // Set the border and box shadow on specific inputs to match
  .form-control {
    border-color: @border-color;
    .box-shadow(inset 0 1px 1px rgba(0,0,0,.075)); // Redeclare so transitions work
    &:focus {
      border-color: darken(@border-color, 10%);
      @shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 6px lighten(@border-color, 20%);
      .box-shadow(@shadow);
    }
  }
  // Set validation states also for addons
  .input-group-addon {
    color: @text-color;
    border-color: @border-color;
    background-color: @background-color;
  }
  // Optional feedback icon
  .form-control-feedback {
    color: @text-color;
  }
}


// Form control focus state
//
// Generate a customized focus state and for any input with the specified color,
// which defaults to the `@input-border-focus` variable.
//
// We highly encourage you to not customize the default value, but instead use
// this to tweak colors on an as-needed basis. This aesthetic change is based on
// WebKit's default styles, but applicable to a wider range of browsers. Its
// usability and accessibility should be taken into account with any change.
//
// Example usage: change the default blue border and shadow to white for better
// contrast against a dark gray background.
.form-control-focus(@color: @input-border-focus) {
  @color-rgba: rgba(red(@color), green(@color), blue(@color), .6);
  &:focus {
    border-color: @color;
    outline: 0;
    .box-shadow(~"inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px @{color-rgba}");
  }
}

// Form control sizing
//
// Relative text size, padding, and border-radii changes for form controls. For
// horizontal sizing, wrap controls in the predefined grid classes. `<select>`
// element gets special love because it's special, and that's a fact!
.input-size(@input-height; @padding-vertical; @padding-horizontal; @font-size; @line-height; @border-radius) {
  height: @input-height;
  padding: @padding-vertical @padding-horizontal;
  font-size: @font-size;
  line-height: @line-height;
  border-radius: @border-radius;

  select& {
    height: @input-height;
    line-height: @input-height;
  }

  textarea&,
  select[multiple]& {
    height: auto;
  }
}

````
<a id="progress-bar"></a>
### 位置progress-bar.less
````html
.progress-bar-variant(@color) {
  background-color: @color;

  // Deprecated parent class requirement as of v3.2.0
  .progress-striped & {
    #gradient > .striped();
  }
}
````
<a id="table-row"></a>
### 位置table-row.less
````html
.table-row-variant(@state; @background) {
  // Exact selectors below required to override `.table-striped` and prevent
  // inheritance to nested tables.
  .table > thead > tr,
  .table > tbody > tr,
  .table > tfoot > tr {
    > td.@{state},
    > th.@{state},
    &.@{state} > td,
    &.@{state} > th {
      background-color: @background;
    }
  }

  // Hover states for `.table-hover`
  // Note: this is not available for cells or rows within `thead` or `tfoot`.
  .table-hover > tbody > tr {
    > td.@{state}:hover,
    > th.@{state}:hover,
    &.@{state}:hover > td,
    &:hover > .@{state},
    &.@{state}:hover > th {
      background-color: darken(@background, 5%);
    }
  }
}

````