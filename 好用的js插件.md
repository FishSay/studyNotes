

## dialog(基于zepto/jq)

[dialog](http://sufangyu.github.io/project/dialog2/dist/demos/)

### 特性

- 支持常见的 alert、confirm、toast、notice 四种类型弹窗
- 可选择使用 IOS 或者 Material Design 风格的弹窗
- 可自定义按钮的文字、样式、回调函数，支持多个按钮
- 多个弹窗状态改变回调函数
- 同时支持 jQuery 和 Zepto 库
- 可扩展性强


  ### 兼容性

- Chrome、Firefox 22+、Opera 9+、Safari、IE10+
- Android 4.0+ (Android 2.3 弹窗动画不够顺畅)
- iOS 8+

### 使用

#### 1、引入 CSS 文件

```
<link rel="stylesheet" href="../css/dialog.css" />
```

#### 2、引入 JS 文件

```
<script src="../lib/zepto.min.js"></script>
<script src="../js/dialog.js"></script>
```

#### 3、HTML 结构

```
<button id="btn-01">显示弹窗</button>
```

#### 4、实例化

```
$(document).on('click', '#btn-01', function() {
    var dialog1 = $(document).dialog({
        content: 'Dialog 移动端弹窗插件的自定义提示内容',
    });
});
```

### 参数

| 参数               | 默认值    | 说明                                                         |
| ------------------ | --------- | ------------------------------------------------------------ |
| type               | 'alert'   | 弹窗的类型。alert: 确定; confirm: 确定/取消; toast: 状态提示; notice: 提示信息 |
| style              | 'default' | alert 与 confirm 弹窗的风格。 default: 根据访问设备平台; ios: ios 风格; android: MD design 风格 |
| titleShow          | true      | 是否显示标题                                                 |
| titleText          | '提示'    | 标题文字                                                     |
| closeBtnShow       | false     | 是否显示关闭按钮                                             |
| content            | ''        | 弹窗提示内容, 值可以是 HTML 内容                             |
| contentScroll      | true      | alert 与 confirm 弹窗提示内容是否限制最大高度, 使其可以滚动  |
| dialogClass        | ''        | 弹窗自定义 class                                             |
| autoClose          | 0         | 弹窗自动关闭的延迟时间(毫秒)。 0: 不自动关闭; 大于0: 自动关闭弹窗的延迟时间 |
| overlayShow        | true      | 是否显示遮罩层                                               |
| overlayClose       | false     | 是否可以点击遮罩层关闭弹窗                                   |
| buttonStyle        | 'side'    | 按钮排版样式。side: 并排; stacked: 堆叠                      |
| buttonTextConfirm  | '确定'    | 确定按钮文字                                                 |
| buttonTextCancel   | '取消'    | 取消按钮文字                                                 |
| buttonClassConfirm | ''        | 确定按钮自定义 class                                         |
| buttonClassCancel  | ''        | 取消按钮自定义 class                                         |
| buttons            | []        | confirm 弹窗自定义按钮组, 会覆盖"确定"与"取消"按钮;  单个 button 对象可设置 name [ 名称 ]、class [ 自定义class ]、callback [ 点击执行的函数 ] |
| infoIcon           | ''        | toast 与 notice 弹窗的提示图标, 值为图标的路径。不设置=不显示 |
| infoText           | ''        | toast 与 notice 弹窗的提示文字, 会覆盖 content 的设置        |
| position           | 'center'  | notice 弹窗的位置, center: 居中; bottom: 底部                |

### 回调函数

| 函数              | 默认值       | 说明                     |
| ----------------- | ------------ | ------------------------ |
| onClickConfirmBtn | function(){} | 点击“确定”按钮的回调函数 |
| onClickCancelBtn  | function(){} | 点击“取消”按钮的回调函数 |
| onClickCloseBtn   | function(){} | 点击“关闭”按钮的回调函数 |
| onBeforeShow      | function(){} | 弹窗显示前的回调函数     |
| onShow            | function(){} | 弹窗显示后的回调函数     |
| onBeforeClosed    | function(){} | 弹窗关闭前的回调函数     |
| onClosed          | function(){} | 弹窗关闭后的回调函数     |

### 方法

| 方法       | 说明                                                         |
| ---------- | ------------------------------------------------------------ |
| obj.close  | 关闭对话框。 用法：dialogObj.close()                         |
| obj.update | 更改 toast 和 notice 类型弹窗内容 ( 图标以及提示文字 ) 可传入参数： content: 弹窗内容, 可以是HTML  infoIcon: 弹窗提示图标 infoText: 弹窗提示文字 autoClose: 自动关闭的延迟时间 onBeforeClosed: 关闭前回调函数 onClosed: 关闭后回调函数 |

### 例子

1. 默认

```
$(document).on('click', '#btn-01', function() {
    $(document).dialog({
        content: '我是默认的弹窗。这里是提示信息内容',
    });
});
```

2. 自定义标题

```
$(document).on('click', '#btn-02', function() {
    $(document).dialog({
        titleText: '我是自定义标题',
        content: '自定义标题的弹窗。这里是弹窗的提示信息内容',
    });
});
```

3. 无标题

```
$(document).on('click', '#btn-03', function() {
    $(document).dialog({
        titleShow: false,
        content: '无标题的弹窗。这里是弹窗的提示信息内容',
    });
});
```

4. 自动关闭

```
$(document).on('click', '#btn-04', function() {
    $(document).dialog({
        autoClose: 2500,
        content: '自动关闭的弹窗。这里是弹窗的提示信息内容',
    });
});
```

5. 点遮罩层关闭

```
$(document).on('click', '#btn-05', function() {
    $(document).dialog({
        overlayClose: true,
        content: '可以点击遮罩层关闭的弹窗。这里是弹窗的提示信息内容',
    });
});
```

6. comfirm

```
$(document).on('click', '#btn-06', function() {
    $(document).dialog({
        type: 'comfirm',
        content: 'confirm 类型的弹窗。这里是弹窗的提示信息内容',
    });
});
```

7. comfirm，自定义按钮文字

```
$(document).on('click', '#btn-07', function() {
    $(document).dialog({
        type : 'confirm',
        titleText: '发现新版本'
        content: '修复低版本安卓手机点透以及无法居中显示问题；去除CSS3启用GPU硬件加速',
        buttonTextConfirm: '现在升级',
        buttonTextCancel: '下次再说',
    });
});
```

8. ### Comfirm 类型, 自定义按钮class

```
$(document).on('click', '#btn-08', function() {
    $(document).dialog({
        type : 'confirm',
        content: 'confirm 类型的弹窗。这里是弹窗的提示信息内容',
        buttonClassConfirm: 'custom-confirm',
        buttonClassCancel: 'custom-cancel',
    });
});
```

9. ### Comfirm 类型, 自定义按钮class

```
$(document).on('click', '#btn-08', function() {
    $(document).dialog({
        type : 'confirm',
        content: 'confirm 类型的弹窗。这里是弹窗的提示信息内容',
        buttonClassConfirm: 'custom-confirm',
        buttonClassCancel: 'custom-cancel',
    });
});
```

10. ### Comfirm 类型, 按钮回调函数

```
$(document).on('click', '#btn-09', function() {
    $(document).dialog({
        type : 'confirm',
        closeBtnShow: true,
        content: 'confirm 类型的弹窗。这里是弹窗的提示信息内容',
        onClickConfirmBtn: function(){
            alert('你点了“确定”按钮');
        },
        onClickCancelBtn : function(){
            alert('你点了“取消”按钮');
        },
        onClickCloseBtn  : function(){
            alert('你点了“关闭”按钮');
        }
    });
});
```

11. ### Comfirm 类型, 状态回调函数

```
$(document).on('click', '#btn-10', function() {
    $(document).dialog({
        type : 'confirm',
        content: 'confirm 类型的弹窗。这里是弹窗的提示信息内容',
        onBeforeShow: function() {
            alert('弹窗显示前执行~~');
        },
        onShow: function() {
            alert('弹窗显示后执行~~');
        },
        onBeforeClosed: function() {
            alert('弹窗关闭前执行~~');
        },
        onClosed: function() {
            alert('弹窗关闭后执行~~');
        }
    });
});
```

12. ### 弹窗风格（按设备，ios，android）

```
$(document).on('click', '#btn-style-01', function() {
    $(document).dialog({
        type : 'confirm',
        style: 'default',  // default、ios、android
        titleText: '弹窗风格',
        content: '按访问设备显示的弹窗风格，这里是弹窗的提示信息内容',
    });
});
```

13. ### 自定义多个按钮

```
$(document).on('click', '#btn-buttons-02', function() {
    $(document).dialog({
        type : 'confirm',
        style: 'android',
        titleText: '发现新版本',
        content: '修复低版本安卓手机点透以及无法居中显示问题；去除CSS3启用GPU硬件加速',
        buttons: [          
            {
                name: '不再提醒',
                callback: function() {
                    alert('你选择了“不再提醒”');
                }
            },
            {
                name: '下次再说',
                callback: function() {
                    alert('你选择了“下次再说”');
                }
            },
            {
                name: '现在升级',
                class: 'dialog-btn-hl',
                callback: function() {
                    alert('你选择了“现在升级”');
                }
            }
        ]
    });
});
```

14. ### 按钮排版样式

```
$(document).on('click', '#btn-buttonStyle-01', function() {
    $(document).dialog({
        type : 'confirm',
        style: 'ios',
        titleText: '发现新版本',
        content: '修复低版本安卓手机点透以及无法居中显示问题；去除CSS3启用GPU硬件加速',
        buttonStyle: 'stacked',  // side: 并排; stacked: 堆叠
        buttons: [
            { name: '现在升级' },
            { name: '下次再说' },
            { name: '不再提醒' }
        ]
    });
});
```

15. ### Toast 类型（加载中，成功，失败，纯图标）

```
$(document).on('click', '#btn-11', function() {
    $(document).dialog({
        type : 'toast',
        infoIcon: '../images/icon/loading.gif',
        infoText: '正在加载中',
        autoClose: 2500
    });
});
```

16. ### Toast 类型, content创建内容（加载中）

```
$(document).on('click', '#btn-15', function() {
    $(document).dialog({
        type : 'toast',
        content: '<img class="info-icon" src="../images/icon/loading.gif" /><span class="info-text">正在加载中</span>',
        autoClose: 2500
    });
});
```

17. ### Toast 类型, 状态更改（加载中to成功）

```
$(document).on('click', '#btn-16', function() {
    var toast5 = $(document).dialog({
        type : 'toast',
        infoIcon: '../images/icon/loading.gif',
        infoText: '正在加载中',
    });

    setTimeout(function () {
        toast5.update({
            infoIcon: '../images/icon/success.png',
            infoText: '加载成功',
            autoClose: 2500,
        });
    }, 3000);
});
```

18. ### Toast 类型, 弹窗类型更改（toast to modal）

```
$(document).on('click', '#btn-17', function() {
    var toast6 = $(document).dialog({
        type : 'toast',
        infoIcon: '../images/icon/loading.gif',
        infoText: '正在加载中',
    });

    setTimeout(function () {
        toast6.close();
        $(document).dialog({
            content: '加载失败！请重新再试',
        });
    }, 2500);
});
```

19. ### Notice 类型（图标+文字，纯文字，纯图标，底部显示）

```
$(document).on('click', '#btn-17', function() {
    $(document).dialog({
        type : 'notice',
        infoIcon: '../images/icon/loading.gif',
        infoText: '正在加载中',
        autoClose: 2500
    });
});

$(document).on('click', '#btn-21', function() {
    $(document).dialog({
        type : 'notice',
        infoText: '正在提交中',
        autoClose: 2500,
        position: 'bottom'  // center: 居中; bottom: 底部
    });
});
```

20. ### Notice 类型，content创建内容（提交中）

```
$(document).on('click', '#btn-22', function() {
    $(document).dialog({
        type : 'notice',
        content: '<img class="info-icon" src="../images/icon/loading.gif" alt="" /><span class="info-text">正在提交中</span>',
        autoClose: 2500
    });
});
```

21. ### Notice 类型，状态更改（提交中to成功）

```
$(document).on('click', '#btn-23', function() {
    var notice5 = $(document).dialog({
        type : 'notice',
        infoIcon: '../images/icon/loading.gif',
        infoText: '正在加载中'
    });

    setTimeout(function () {
        notice5.update({
            infoIcon: '../images/icon/success.png',
            infoText: '加载成功！！',
            autoClose: 2500
        });
    }, 3000);
});
```

### 目录结构

```
.
├─dist                # 项目发布资源目录, Grunt 生成
│  ├─css              # 项目 CSS 文件
│  ├─demos            # 项目示例页面
│  ├─images           # 项目 image 文件
│  ├─js               # 项目 JS 文件
│  │  ├─dialog.js     # 弹窗 JS
│  │  ├─dialog.min.js # 弹窗最小版本 JS
│  │  └─example.js    # 示例 JS
│  └─lib              # 公共 JS 文件
│
├─src                 # 实际进行开发的目录
│  ├─css              # 项目 CSS 文件, 由 Grunt 生成
│  ├─demos            # 项目示例页面
│  ├─images           # 项目 image 文件
│  ├─js               # 项目 JS 文件
│  │  ├─dialog.js     # 弹窗主要 JS
│  │  ├─example.js    # 示例 JS
│  │  ├─ripple.js     # 点击水波纹效果 JS
│  │  └─tapEvent.js   # 点击事件 JS
│  ├─lib              # 公共 JS 文件
│  ├─scss             # 项目相关 SCSS 文件
│  └─templates        # 初始静态 DMEO 资源目录
│
├─Gruntfile.js        # Grunt任务配置
├─_config.json        # Grunt配置所需信息
└─package.json        # 项目信息以及依赖
```

## 上拉刷新，下拉加载（dropload）

### 使用

```html
<link rel="stylesheet" href="../dist/dropload.css">
<script src="../dist/dropload.min.js"></script>
```



示例

```javascript
   <div id="content"></div>


$('#content').dropload({
      scrollArea: window,
      domDown: {
        domClass: 'dropload-down',
        domRefresh: '<div class="dropload-refresh">↑上拉加载更多</div>',
        domLoad:
          '<div class="dropload-load"><span class="loading"></span>加载中...</div>',
        domNoData: '<div class="dropload-noData">暂无数据</div>'
      },
      loadDownFn: function(me) {
        $.ajax({
          type: 'GET',
          url: './more.json',
          dataType: 'json',
          success: function(data) {
            if (data.lists.length > 0) {
              var result = '';
              for (var i = 0; i < data.lists.length; i++) {
                result +=
                  '<a class="item opacity" href="' +
                  data.lists[i].link +
                  '">' +
                  '<img src="' +
                  data.lists[i].pic +
                  '" alt="">' +
                  '<h3>' +
                  data.lists[i].title +
                  '</h3>' +
                  '<span class="date">' +
                  data.lists[i].date +
                  '</span>' +
                  '</a>';
              }
            } else {
              // 如果没有数据
              //锁定
              me.lock();
              // 无数据
              me.noData();
            }
            // 为了测试，延迟2秒加载
            setTimeout(function() {
              $('.dropload-down').before(result);
              // 每次数据加载完，必须重置
              me.resetload();
            }, 2000);
          },
          error: function(xhr, type) {
            alert('Ajax error!');
            // 即使加载出错，也得重置
            me.resetload();
          }
        });
      }
    });
```

### 参数列表

| 参数       | 说明         | 默认值                                                       | 可填值                                     |
| ---------- | ------------ | ------------------------------------------------------------ | ------------------------------------------ |
| scrollArea | 滑动区域     | 绑定元素自身                                                 | window                                     |
| domUp      | 上方DOM      | { domClass : 'dropload-up', domRefresh : '<div class="dropload-refresh">↓下拉刷新</div>', domUpdate  : '<div class="dropload-update">↑释放更新</div>', domLoad : '<div class="dropload-load">○加载中...</div>' } | 数组                                       |
| domDown    | 下方DOM      | { domClass : 'dropload-down', domRefresh : '<div class="dropload-refresh">↑上拉加载更多</div>', domLoad : '<div class="dropload-load">○加载中...</div>', domNoData : '<div class="dropload-noData">暂无数据</div>' } | 数组                                       |
| autoLoad   | 自动加载     | true                                                         | true和false                                |
| distance   | 拉动距离     | 50                                                           | 数字                                       |
| threshold  | 提前加载距离 | 加载区高度2/3                                                | 正整数                                     |
| loadUpFn   | 上方function | 空                                                           | function(me){ //你的代码 me.resetload(); } |
| loadDownFn | 下方function | 空                                                           | function(me){ //你的代码 me.resetload(); } |

### API

暴露一些功能，可以让dropload更灵活的使用

lock() 锁定dropload

| 参数         | 说明                           |
| ------------ | ------------------------------ |
| lock()       | 智能锁定，锁定上一次加载的方向 |
| lock('up')   | 锁定上方                       |
| lock('down') | 锁定下方                       |

unlock() 解锁dropload

noData() 无数据

| 参数          | 说明   |
| ------------- | ------ |
| noData()      | 无数据 |
| noData(true)  | 无数据 |
| noData(false) | 有数据 |

### 已知问题

由于部分Android中UC和QQ浏览器头部有地址栏，并且一开始滑动页面隐藏地址栏时，无法触发scroll和resize，所以会导致部分情况无法使用。解决方案1：增加distance距离，例如DEMO2中distance:50；解决方案2：加meta使之全屏显示

```html
`<``meta` `name``=``"full-screen"` `content``=``"yes"``>``<``meta` `name``=``"x5-fullscreen"` `content``=``"true"``>`
```

## 点击图片放大（photoswipe）

**此为基于原生的插件**

[github](https://github.com/dimsemenov/photoswipe)



# 原生js alert,prompt,confirm

[PostbirdAlertBox.js](https://github.com/postbird/PostbirdAlertBox.js)

