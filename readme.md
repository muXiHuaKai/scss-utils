# scss-utils


主要收录项目开发中一些常用的样式、mixin等，方便使用

目前收录：
---
***单行文本不换行***
```
.no-wrap {
    text-overflow: ellipsis;
    overflow: hidden;
    white-space: nowrap;
}
```
***扩展点击区域（移动端适用）***
```
.extend-click {
    position: relative;
    &:before {
        content: "";
        position: absolute;
        top: -10px;
        left: -10px;
        right: -10px;
        bottom: -10px;
    }
}
```

***禁止选中***
```
.no-select {
    user-select: none;
}
```

***禁止点击***
```
.no-click {
    pointer-events: none;
}
```

***多行文本省略号(默认两行)***
```
@mixin mul-line($line: 2) {
    overflow: hidden;
    word-break: break-all;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: $line;
    -webkit-box-orient: vertical;
}

/*
usage: 
    .txt{
        @include mul-line(3) // 只显示三行，超出显示省略号
    }
*/
```

***自定义placeholder样式***
```
@mixin self-placeholder($fz: 16px, $color: #999, $align: left) {
    &:-moz-placeholder {
        font-size: $fz;
        color: $color;
        text-align: $align;
    }
    &:-ms-input-placeholder {
        font-size: $fz;
        color: $color;
        text-align: $align;
    }
    &:-webkit-input-placeholder {
        font-size: $fz;
        color: $color;
        text-align: $align;
    }
}
```

***自定义文本选中样式***
```
@mixin self-select($color: #999, $bgColor: #eee) {
    &::selection {
        color: $color;
        background-color: $bgColor;
    }
}
```

***1px 边框***
>作者：铁皮饭盒
>
>链接：https://juejin.im/post/5d70a030f265da03a715f3fd
>
>来源：掘金
>
>著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```
@mixin thinBorder($directionMaps: bottom,$color: #ccc,$radius: (0,0, 0,0),$position: after)
```

使用：
```
//单侧边框
//生成.border-top-1px等4个单侧边框;
@each $dir in (top,right,bottom,left) {
  .border-#{$dir}-#{1}px {
    @include thinBorder( $dir);
  }
}

//多侧边框
//生成"红色"的多侧边框 .border-top-left-red-1px
.border-top-left-red-1px{
  @include thinBorder((top,left), red);
}

//圆角边框
//生成带100px圆角的边框 .border-top-left-round-1px
.border-top-left-red-1px{
  @include thinBorder(top, red, 100px);
}

//使用:before去生成边框
.border-top-before{
  @include thinBorder(top, red, 0, before);
}
```

---
<small>不定时持续更新<small>