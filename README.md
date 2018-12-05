# zoo-lazyload

政采云懒加载组件，轻松实现懒加载+图片优化.基于可配置的图片属性，实现自动添加阿里云cdn压缩后缀，支持webp。基于[vanilla-lazyload](https://www.andreaverlicchi.eu/lazyload/)8.17.0定制。

##使用方法

##### 简单使用

引入js: `<script src="https://sitecdn.zcy.gov.cn/zcy-front-other-upload/3f06ad2205c80c2b8201c3dc3e29b417.js"></script>`

Import: `import LazyLoad from 'zoo-lazyload'; `

```html
<img class="lazyload" data-src="./img/img.jpg" alt="图片名称" width="100" height="100" />
```

```javascript
// 传入需要懒加载的图片class
new LazyLoad('.lazyload');
// 或者
new LazyLoad({
    elements_selector: '.lazyload',
    dpr: 2,
});
```

##### [详细配置文档](https://www.andreaverlicchi.eu/lazyload/)

### 详细配置
* 图片
    * **class**
        * img加lazyload class，此class为LazyLoad的elements_selector配置项。
    * **src**
        * 改为data-src。
    * **width、height**: 设置图片宽高
        * 读取width、height属性作为cdn压缩的后缀。
        * 不设置宽高的话，只可以压缩jpg格式的质量。
    * **data-format**: 设置图片类型:
        * png： 图片转为png格式。
        * jpg: 图片格式改为jpg。默认是jpg格式，所以此选项可不写。
        * 1或其他：不改变原来图片格式
            * 如果图片需要透明背景，则不可压缩质量，只能改变尺寸。请添加data-format="1"属性，这样js就不会在不支持webp的浏览器中加jpg后缀了
    * **data-q**: 压缩质量
        * 默认为75， 可通过data-q设置<img data-q="80" />修改压缩质量, 取值为60-100之间的整数
    * **data-dpr**:  倍图设置
        * 可在图片上data-dpr="2"来配置2倍或其他数字。
* 背景图
    * 需要背景透明：不修改
    * 不需要背景透明：加后缀?x-oss-process=image/quality,Q_75/format,jpg

#### 打包: npm run build

