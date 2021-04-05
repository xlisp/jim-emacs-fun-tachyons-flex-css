# jim-emacs-fun-tachyons-flex-css Functional CSS的列表(tachyons css)

- [jim-emacs-fun-tachyons-flex-css Functional CSS的列表(tachyons css)](#jim-emacs-fun-tachyons-flex-css-functional-css%E7%9A%84%E5%88%97%E8%A1%A8tachyons-css)
  - [相关资源](#%E7%9B%B8%E5%85%B3%E8%B5%84%E6%BA%90)
    - [python函数式的列表](#python%E5%87%BD%E6%95%B0%E5%BC%8F%E7%9A%84%E5%88%97%E8%A1%A8)
    - [JavaScript函数式的列表](#javascript%E5%87%BD%E6%95%B0%E5%BC%8F%E7%9A%84%E5%88%97%E8%A1%A8)
  - [良好的第一性原则](#%E8%89%AF%E5%A5%BD%E7%9A%84%E7%AC%AC%E4%B8%80%E6%80%A7%E5%8E%9F%E5%88%99)
  - [水平布局](#%E6%B0%B4%E5%B9%B3%E5%B8%83%E5%B1%80)
  - [垂直布局](#%E5%9E%82%E7%9B%B4%E5%B8%83%E5%B1%80)
  - [垂直居中](#%E5%9E%82%E7%9B%B4%E5%B1%85%E4%B8%AD)
  - [水平居中](#%E6%B0%B4%E5%B9%B3%E5%B1%85%E4%B8%AD)
  - [位置至底](#%E4%BD%8D%E7%BD%AE%E8%87%B3%E5%BA%95)
  - [flex-auto弹性平分](#flex-auto%E5%BC%B9%E6%80%A7%E5%B9%B3%E5%88%86)
  - [Herb表达CSS伪元素](#herb%E8%A1%A8%E8%BE%BEcss%E4%BC%AA%E5%85%83%E7%B4%A0)
  - [Herb使用多个CSS函数](#herb%E4%BD%BF%E7%94%A8%E5%A4%9A%E4%B8%AAcss%E5%87%BD%E6%95%B0)
  - [底部导航栏](#%E5%BA%95%E9%83%A8%E5%AF%BC%E8%88%AA%E6%A0%8F)
  - [搜索框内部任意位置加一个图标](#%E6%90%9C%E7%B4%A2%E6%A1%86%E5%86%85%E9%83%A8%E4%BB%BB%E6%84%8F%E4%BD%8D%E7%BD%AE%E5%8A%A0%E4%B8%80%E4%B8%AA%E5%9B%BE%E6%A0%87)
  - [debug.css](#debugcss)

## 相关资源
### [python函数式的列表](https://github.com/FPTensorFlow/jim-emacs-fun-py)
### [JavaScript函数式的列表](https://github.com/chanshunli/jim-emacs-fun-es6)

## 良好的第一性原则
* 尽量用padding撑开div盒子(每个盒子撑满的感觉),减少用margin(除非盒子与盒子之间,margin外边距,比较难调,会很乱), 外面格子撑满,里面才好处理,外面不要pa
* 尽量用em,其次是 vh高/vw宽, 最后才是px
* 用[Herb](http://herb.roosta.sh)复用CSS,把CSS当函数来用,来提高CSS的表达速度: `复用的速度^2 = 几何爆炸式的表达速度`
* 调试CSS: 使用debug.css,或者是background设置成特殊颜色来判断盒子的层级和关系是否正确(所有可视的div都给颜色是个好习惯)
* 第一原理裸奔不用框架而是用最基础的css原理(越来越快，几何速度上升)和复用(平方等于复利): 重新自己写一遍css的时候，你就能最高效的复用，否则你抄别人的怎么都抄不对; 抄来抄去一辈子都进步不了，一辈子都自己写不出来复杂的页面
* 你尝试那么多次,还不如撸一遍文档来得更快
* 一边写样式的元解释器,一边写代码 => 最高速的大脑流 => Repl本质就是元解释器 ## nginx -t解释器 加 vi 修改检测 => Emacs hook mode
* 递归 relative相对定位 => absolute绝对定位 => relative 相对定位 => absolute 绝对定位 。。。

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

## 水平居中

``` clojure
[:div.bg-yellow
 {:style {:height "15em"}}
 [:div.h-100.flex
  [:div.flex.justify-center.align-center
   [:img {:style {:height "15em"}
          :src "/img/openRightMini.svg"}]]]]
```

## 垂直居中

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

;;需要宽度才能居中
[:div.b.f4.flex.justify-center.items-center
 {:style
  {:width "10em"}}
 [:div "ABC"]]

;; 先不要绝对定位浮在上面, 等整体div调好之后，再加上绝对定位 ## absolute之外不能再有absolute,否则会失效
[:div.flex.justify-center.items-center.absolute
     {:style {:width "100vw" ;; 下面的50vw居中了
              :top "5em"}}
     ;; .flex.items-center.justify-center
     ;; {:style {:width "100%"
     ;;          :top "5em"}}
     [:div.br3.flex.flex-column
      {:style {:z-index 9000 ;; 比alert更低一点
               :width "50vw"
               :background c/white
               }}
 [:div 局部div]
 [:div 局部div]
 [:div 局部div]
]]
```

## 位置至底

``` clojure
(defn button-style [{:keys [stri on-click]}]
  [:div.flex.justify-end.items-end
   [:button.f6.ba.bg-white
    {:on-click on-click
     :style {:border-radius "1em"
             :height "2em"
             :background "#de171a"
             :color "white"
             :width "5.5em"}}
    stri]])
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

[herb.core :refer [<class join]]


(defn mutil-color []
  {:color "#09f"})

(defn msg-style []
  ^{:pseudo {:after {:content "' '"
                     :border-left-color "#b2e281"
                     :border-left-width "4px"}}}
  {:border-radius "5px"
   :background-color "#b2e281"})

[:div {:class (join
                (<class msg-style)
                (<class mutil-color))}
 [:div {:style {:background "./img/voice.png"}}]
 "ABC"]
```

## 底部导航栏

``` clojure

(defn foot-item [text icon-path]
  [:div.flex-auto.flex.flex-column.items-center.justify-between
   [:div text]
   [:img.h2 {:src icon-path}]])

[:div.absolute.bottom-0.h3.pa3.flex.flex-row.items-center.w-100.bg-near-white.bt.b--moon-gray
  [foot-item "首页" "img/home.svg"]
  [foot-item "我的" "img/profile.svg"]]

;;把foot浮动撑到最低,但保持不动
(defn fullscreen [& body]
  [:div.relative.vw-100.vh-100
   (into [:div.absolute.top-0.bottom-0.left-0.right-0.flex.flex-column]
     body)])
```

## 搜索框内部任意位置加一个图标

``` clojure
[:div.w-100.white.bb.f3.relative.h3.flex.flex-column.justify-center.bg-white
 [:input.br-pill.h2.mh2.ph3.f6]
 [:div.flex.flex-row.absolute.w-100.h-100.items-center.justify-center
  {:style {:pointer-events :none}}
  [:div [:img {:style {:width ".5em"}
               :src "/img/search.svg"}]]
  [:div.silver.f5
   "搜索"]]]
```

## 递归 relative相对定位 => absolute绝对定位
```clojure
(if @right-open-status
  ;; 相对于整体某个位置的相对定位
  [:div.relative
   [right-dot-menu]]
  [:nobr])

(defn right-dot-menu []
  ;; 相对上面的相对位置的绝对定位
  [:div.absolute {:style {:top "0"
                          :left  "0.2em"}}
   [:div.flex.flex-column.bg-white.flex.justify-center.items-center.relative ;; 相对上面的绝对位置的相对定位
    {:on-click nil
     :style
     {:width "6rem"
      :z-index 8888
      :top 0}}
    [:div.pa2 "AAA"]
    [:div.pa2 "BBBB"]
    ;;
    [:div
     [:div.pa2.flex.flex-row
      [:div.flex.flex-auto.mr3 "CCCC"]]
     ;; 弹出来的子级菜单: 绝对定位
     [:div.absolute.bg-white.br2
      {:style {:bottom "0"
               :left "6rem"}}
      [:div.pa2 "123"]
      [:div.pa2 "123"]
      [:div.pa2 "123"]]]
    ;;
    [:div.pa2
     [:div.flex.flex-auto.mr3 "EEEE"]]]])

```

## debug.css

![](https://raw.githubusercontent.com/chanshunli/jim-emacs-fun-tachyons-flex-css/master/debug_css.png)
