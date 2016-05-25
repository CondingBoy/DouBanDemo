# DouBanDemo
熟悉了iewpager，PagerSlidingTabStrip,swipRefresh的使用
在练习中出现的错误以及自己的理解：
>1.设置swipRefresh的颜色应该用这个方法
    
    refreshLayout.setColorSchemeResources

>2.监听swipRefresh的onRefresh事件中，需要设置refresh的状态，这样才不会重复的触发onRefresh事件，并记得在onRefresh执行完后，重新设置Refresh的状态
    
    public void onRefresh() {
          refreshLayout.setRefreshing(true);
          new android.os.Handler().postDelayed(new Runnable() {
              @Override
              public void run() {
                  //三秒过后，用户可以重新刷新,在实际开发中这里是在网络数据返回后才关闭的
                  refreshLayout.setRefreshing(false);
              }
          }, 3000);
      }
  
>3.在使用FragmentPagerAdpager时需要返回的是supportV4包中的Fragment，所以Activity需要继承FragmentActivity

>4.在使用第三方控件时，在布局文件中需要加上一个命名空间，这样才能使用这个控件的自定义属性

     xmlns:app="http://schemas.android.com/apk/res-auto"
