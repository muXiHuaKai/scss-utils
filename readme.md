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


---
<small>不定时持续更新<small>