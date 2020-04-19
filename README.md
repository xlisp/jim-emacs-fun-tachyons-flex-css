# jim-emacs-fun-tachyons-flex-css Functional CSS的列表(tachyons css)

- [jim-emacs-fun-tachyons-flex-css Functional CSS的列表(tachyons css)](#jim-emacs-fun-tachyons-flex-css-functional-css%E7%9A%84%E5%88%97%E8%A1%A8tachyons-css)
  - [相关资源](#%E7%9B%B8%E5%85%B3%E8%B5%84%E6%BA%90)
    - [python函数式的列表](#python%E5%87%BD%E6%95%B0%E5%BC%8F%E7%9A%84%E5%88%97%E8%A1%A8)
    - [JavaScript函数式的列表](#javascript%E5%87%BD%E6%95%B0%E5%BC%8F%E7%9A%84%E5%88%97%E8%A1%A8)
  - [水平布局](#%E6%B0%B4%E5%B9%B3%E5%B8%83%E5%B1%80)
  - [垂直布局](#%E5%9E%82%E7%9B%B4%E5%B8%83%E5%B1%80)
  - [垂直居中](#%E5%9E%82%E7%9B%B4%E5%B1%85%E4%B8%AD)
  - [水平居中](#%E6%B0%B4%E5%B9%B3%E5%B1%85%E4%B8%AD)

## 相关资源
### [python函数式的列表](https://github.com/FPTensorFlow/jim-emacs-fun-py)
### [JavaScript函数式的列表](https://github.com/chanshunli/jim-emacs-fun-es6)

## 良好的第一性原则
* 尽量用padding撑开div盒子,减少用margin(除非盒子与盒子之间)
* 尽量用em,其次是 vh高/vw宽, 最后才是px
* 用[Herb](http://herb.roosta.sh)复用CSS,把CSS当函数来用,来提高CSS的表达速度: `复用的速度^2 = 几何爆炸式的表达速度`
* 调试CSS: 使用debug.css,或者是background设置成特殊颜色来判断盒子的层级和关系是否正确

## 水平布局

``` clojure
[:div.flex.flex-row
 [:div]
 [:div]]
```

## 垂直布局

``` clojure
[:div.flex.flex-column
 [:div]
 [:div]]
```

## 垂直居中

``` clojure
[:div.bg-yellow
 {:style {:height "15em"}}
 [:div.h-100.flex
  [:div.flex.justify-center.align-center
   [:img {:style {:height "15em"}
          :src "/img/openRightMini.svg"}]]]]
```

## 水平居中

``` clojure
[:div.justify-center.items-center
 [:div.flex.flex-row.pa3.pb1.pt4
  [:div.gray.b.f3.flex.justify-center.items-center
   {:style {:flex 1}}
   "A"]
  [:div.gray.b.f3.flex.justify-center.items-center
   {:style {:flex 1}}
   "B"]
  [:div.gray.b.f3.flex.justify-center.items-center
   {:style {:flex 1}}
   "C"]]]
```

## flex-auto弹性平分

``` clojure
;; flex-auto水平平分
[:div.flex.flex-row.pt2.pb3 {:style {:width "10em"}}
 [:div.gray.f5.flex.flex-auto "A"]
 [:div.gray.f5.pl2.flex.flex-auto "B"]
 [:div.gray.f5.pl2.flex.flex-auto "C"]]

;; flex-auto垂直平分
[:div.flex.flex-column.pt2.pb3 {:style {:height "10em"}}
 [:div.gray.f5.flex.flex-auto "A"]
 [:div.gray.f5.pl2.flex.flex-auto "B"]
 [:div.gray.f5.pl2.flex.flex-auto "C"]]

```

## Herb表达CSS伪元素

``` clojure

(defn hover-menu-style []
  ^{:pseudo {:hover {:background "black"
                     :color "white"}}}
  {:color "black"})

;; (:require [herb.core :refer [<class]])

[:div.pa2 {:class (<class css/hover-menu-style)} "搜索"]

```

## Herb使用多个CSS函数

``` clojure

```

## debug.css

![](https://raw.githubusercontent.com/chanshunli/jim-emacs-fun-tachyons-flex-css/master/debug_css.png)
