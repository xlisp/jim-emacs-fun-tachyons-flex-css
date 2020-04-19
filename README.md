# jim-emacs-fun-tachyons-flex-css Functional CSS的列表(tachyons css)

## 相关资源
### [python函数式的列表](https://github.com/FPTensorFlow/jim-emacs-fun-py)
### [JavaScript函数式的列表](https://github.com/chanshunli/jim-emacs-fun-es6)

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
