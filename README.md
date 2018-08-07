# ywh-slidesliprecyclerview
# 作者 杨文浩  Email：672089925@qq.com
# 说明：ywh-slidesliprecyclerview是一个支持侧滑的RecyclerView,目前仅升级左侧滑动,默认滑动查过侧滑布局的一半，会平滑打开item,不超过一半会平滑关闭。
# 1 使用方法:
## 1.1    在项目root build.gradle中添加
<br>    allprojects {
<br>          repositories {
<br>            jcenter()
<br>            maven { url 'https://jitpack.io' }
<br>        }
<br>    }
## 1.2  在app  build.gradle中依赖
<br>     compile 'com.github.yyyangwenhao:ywh-slidesliprecyclerview:v2.0' 

# 2  布局
<br> <ywh.view.SideSlipRecyclerView 
<br>     android:id="@+id/swipeRecyclerView"
<br>     android:layout_width="match_parent" 
<br>     android:layout_height="match_parent"/>
# 3 Activity中使用
<br>  adapter = new SwipeAdapter(this, list);  

<br>  sideSlipRecyclerView.setLayoutManager(new GridLayoutManager(this,2){
<br>      @Override
<br>      public boolean canScrollVertically() {
<br>            //仿微信，侧滑时禁止上下滑动，如不需要，则不需要重写canScrollVertically
<br>          return !sideSlipRecyclerView.getIsScrollingH();      
<br>      }
<br>  });
<br>  sideSlipRecyclerView.setAdapter(adapter);
<br>  // 设置侧滑监听，不写则不会出现侧滑，参数一：需要滑出来的布局id, 参数二：滑动回调接口
<br>  sideSlipRecyclerView.setOnItemSlide(R.id.ll_outside, this);  
                                                                                                            
<br>  实现ywh.view.OnItemSlideListener接口的方法
<br>    @Override
<br>   public void onSlide(final int position, boolean isOpened, View outSideView) {
<br>        //参数一：滑动item的position,参数二item是否打开了，参数三：返回侧滑出来的View    
<br>   }
