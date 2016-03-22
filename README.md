# NineGridView
类似QQ空间，微信朋友圈，微博主页等，展示图片的九宫格控件，自动根据图片的数量确定图片大小和控件大小，使用Adapter模式设置图片，对外提供接口回调，整合了Glide和PhotoView，点击图片全屏预览大图。


该项目是根据：[https://github.com/laobie/NineGridImageView](https://github.com/laobie/NineGridImageView) 修改而成，进行了优化扩展，使代码更加简单，喜欢原作的可以去使用。同时欢迎大家下载体验本项目，如果使用过程中遇到什么问题，欢迎反馈。

## 演示
 ![image](https://github.com/jeasonlzy0216/NineGridView/blob/master/screenshots/demo1.png) ![image](https://github.com/jeasonlzy0216/NineGridView/blob/master/screenshots/demo2.gif) ![image](https://github.com/jeasonlzy0216/NineGridView/blob/master/screenshots/demo3.png) ![image](https://github.com/jeasonlzy0216/NineGridView/blob/master/screenshots/demo4.gif) ![image](https://github.com/jeasonlzy0216/NineGridView/blob/master/screenshots/demo5.png)![image](https://github.com/jeasonlzy0216/NineGridView/blob/master/screenshots/demo6.png)


## 1.项目功能
 * 使用Adapter模式设置图片
 * 当图片数量只有一张时，自动根据图片大小调整控件大小
 * 默认增加了图片点击全屏预览效果，并附带预览动画
 * 整合了Glide图片加载和PhotoView图片预览
 * 使用接口抽出图片的加载方式，可以方便的将Glide替换成自己喜欢的ImageLoader等
 * 使用代码简单，只需要几行代码
 * 其他功能增加中......

## 2.参数含义

<table>
  <tdead>
    <tr>
      <th align="center">自定义属性名字</th>
      <th align="center">参数含义</th>
    </tr>
  </tdead>
  <tbody>
    <tr>
      <td align="center">singleImageSize</td>
      <td align="center">只显示一张图片时的最大图片大小</td>
    </tr>
    <tr>
      <td align="center">singleImageRatio</td>
      <td align="center">只显示一张图片时图片宽高比</td>
    </tr>
    <tr>
      <td align="center">singleImageScaleType</td>
      <td align="center">只显示一张图片时图片的缩放模式</td>
    </tr>
    <tr>
      <td align="center">gridSpacing</td>
      <td align="center">网格显示图片时，图片之间的间距，默认3dp</td>
    </tr>
    <tr>
      <td align="center">maxSize</td>
      <td align="center">最多显示图片的数量，默认最大9张</td>
    </tr>
     </tbody>
</table>

## 代码演示
####使用时只需要在每个条目需要展示的地方用如下代码，其中
 * `ImageInfo`是库中提供的数据Bean，需要两个url，分别表示小图和大图的url，没有大图或者小图，则都赋给相同的Url即可。
 * `ClickNineGridViewAdapter`是库中提供的默认实现了点击预览的Adapter，如果不想使用预览效果，可以自己继承 `NineGridViewAdapter` 实现其中 `onDisplayImage` 方法即可。
```java
	ArrayList<ImageInfo> imageInfo = new ArrayList<>();
    List<EvaluationPic> imageDetails = item.getAttachments();
    if (imageDetails != null) {
        for (EvaluationPic imageDetail : imageDetails) {
            ImageInfo info = new ImageInfo();
            info.setThumbnailUrl(imageDetail.smallImageUrl);
            info.setBigImageUrl(imageDetail.imageUrl);
            imageInfo.add(info);
        }
    }
    holder.nineGrid.setAdapter(new ClickNineGridViewAdapter(context, imageInfo));
```