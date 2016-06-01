# GuideView
新手引导视图，初次打开页面时显示。
支持圆形，椭圆，矩形等多种图形
提示部分支持图片和文字提示

#先看效果图
![image](https://github.com/qiushi123/GuideView-master/blob/master/images/11.jpg?raw=true)



#使用步骤。
###使用起来特别简单，只需要把GuideView这个类复制到你的项目中就可以了


*使用图片

        ImageView iv = new ImageView(this);
        iv.setImageResource(R.drawable.img_new_task_guide);
        RelativeLayout.LayoutParams params = new RelativeLayout.LayoutParams(
            ViewGroup.LayoutParams.WRAP_CONTENT, ViewGroup.LayoutParams.WRAP_CONTENT);
        iv.setLayoutParams(params);

![image](https://github.com/qiushi123/GuideView-master/blob/master/images/a.png?raw=true)

*使用文字

        TextView iv = new TextView(this);
        iv.setText("欢迎使用");
        iv.setTextColor(getResources().getColor(R.color.white));
        
![image](https://github.com/qiushi123/GuideView-master/blob/master/images/b.png?raw=true)

*显示GuideView

        GuideView.Builder
            .newInstance(this)      // 必须调用
            .setTargetView(view)    // 必须调用，设置需要Guide的View
            .setCustomTipsView(iv)  // 必须调用，设置GuideView，可以使任意View的实例，比如ImageView 或者TextView
            .setDirction(GuideView.Direction.LEFT_BOTTOM)   // 设置GuideView 相对于TargetView的位置，有八种，不设置则默认在屏幕左上角,其余的可以显示在右上，右下等等
	    .setShape(GuideView.MyShape.RECTANGULAR)   // 设置显示形状，支持圆形，椭圆，矩形三种样式，矩形可以是圆角矩形，
            .setBackGround(getResources().getColor(R.color.shadow)) // 设置背景颜色，默认透明
            .setOnclickExit(null)   // 设置点击消失，可以传入一个Callback，执行被点击后的操作
            .setRadius(32)          // 设置圆形或矩形透明区域半径，默认是targetView的显示矩形的半径，如果是矩形，这里是设置矩形圆角大小
            .setCenter(300, 300)    // 设置圆心，默认是targetView的中心
            .setOffset(200, 60)     // 设置偏移，一般用于微调GuideView的位置
            .showOnce()             // 设置首次显示，设置后，显示一次后，不再显示
            .build()                // 必须调用，Buider模式，返回GuideView实例
            .show();                // 必须调用，显示GuideView
