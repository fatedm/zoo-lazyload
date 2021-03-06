# @zcy/zoo-lazyload

政采云懒加载组件，轻松实现懒加载+图片优化.基于可配置的图片属性，实现自动添加阿里云cdn压缩后缀，支持webp。基于[vanilla-lazyload](https://www.andreaverlicchi.eu/lazyload/)8.17.0定制。兼容IE9+及标准浏览器。

## 适用场景
* 包含大量图片的页面。
* 图片保存在阿里cdn上。

## DEMO

[Examples](https://sitecdn.zcy.gov.cn/zcy-front-other-upload/eccac4a499a6232eb45ce06b23754f18.html)

## 使用方法

#### 引入

- ###### 简单使用
  - html引入js:

    ```html
    <script src="https://cdn.zcy.gov.cn/zcy-front-other-upload/zoo-lazyload.min.js"></script>
    ```

- ###### import

    ```javascript
    import LazyLoad from '@zcy/zoo-lazyload';
	```



#### html修改

- 图片

  ```html
  <img class="lazyload" data-src="https://sitecdn.zcy.gov.cn/zcy-front-other-upload/4b6ac189a0e1bd6ef4a38091a66f7a61.png" data-srcset="https://sitecdn.zcy.gov.cn/zcy-front-other-upload/4b6ac189a0e1bd6ef4a38091a66f7a61.png 2x" alt="图片名称" width="100" height="100" />
  ```

- 背景图

  ```html
  <div class="lazyload" width="1000" height="500" data-src="https://sitecdn.zcy.gov.cn/zcy-front-other-upload/4b6ac189a0e1bd6ef4a38091a66f7a61.png"></div>
  
  <!-- 或者 -->
  
  <div class="lazyload" width="1000" height="500" data-bg="https://sitecdn.zcy.gov.cn/zcy-front-other-upload/4b6ac189a0e1bd6ef4a38091a66f7a61.png"></div>
  ```



#### 调用

```javascript
// 传入需要懒加载的图片class
new LazyLoad({
    elements_selector: '.lazyload',
});
// 如果是动态插入的图片，需要在图片插入DOM后手动调用new LazyLoad()
```

## [详细配置文档](https://www.andreaverlicchi.eu/lazyload/)

### 详细配置
* 图片/背景图
    * **class**
        * 加lazyload class，此class为LazyLoad的elements_selector配置项。
    * **src**
        * 改为data-src，背景图可设置data-bg="url(图片地址)".
    * **data-l**
        * 最大边
    * **data-m-pad**
        * data-l、width或height设置后，是否补白，默认补白为白色.
    * **data-color**
        * 当设置data-m-pad后，补白的十六进制颜色，如FF0000(必须6位，不支持3位缩写)。
    * **width、height**: 设置图片宽高
        * 读取width、height属性作为cdn压缩的后缀。
        * 不设置宽高的话，只可以压缩jpg格式的质量。
    * **data-format**: 设置图片类型:
        * png： 图片转为png格式。
        * jpg: 图片格式改为jpg。默认是jpg格式，所以此选项可不写。
        * 1或其他：不改变原来图片格式
            * 如果图片需要透明背景，则不可压缩质量，只能改变尺寸。请添加data-format="1"属性，这样js就不会在不支持webp的浏览器中加jpg后缀了
    * **data-q**: 压缩质量
        * 默认为75， 可通过data-q设置修改压缩质量, 取值为60-100之间的整数
    * **data-dpr**:  倍图设置
        * 设置data-dpr="2"来配置2倍或其他数字。



## 常见问题

- 图片没加载出来

  - 核查js是否引入，class是否写错，是否调用new LazyLoad。

  - 如果是背景图，确认调用方式如下

    ```javascript
    new LazyLoad({
        elements_selector: '.lazyload',
    });
    ```

  - 动态插入的图片需要在图片插入DOM后手动执行new LazyLoad。