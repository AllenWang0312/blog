
## SafeArea

## Expanded 
    使colum 或 row 的某个子项填充剩余空间
    类似 android:weight

## Wrap

## AnimatedContainer 
    动画容器
    通过setState() 改变某个属性值 会自动为其添加动画

## Opacity (不透明度)  Visibility=GONE
    Opacity(
        opacity:0.0,
        child:MyWidget(Colors.blue),
    )
## FutureBuilder 
    异步执行任务 根据处理结果显示布局   

    FutureBuilder(
        future:http.get('http://awesome.data'),
        huilder:(context,snapshot){
            if(snapshot.connectionState == ConnectionState.done){//none/waiting/active/donn
                if(snapshot.hasError){
                return ...
                }
                return AwesomeData(snapshot.data);
            }else{
                return CircularProgressIndicator();
            }
        }
    )
## FadeTransition
    
    见 flutter_lms/lib/common/my_fade_in.dart
## FloatingActionButton 
    Scaffold(
        floatingActionButton:...
        buttomNavigationBar:...
        floatingActionButtonLocation:FloatingActionButtonLocation.centerDocked,
    )
## PageView (ViewPager)
    Final pageView = PageView(
    controller:controller,
    //scrollDirection:Axis.vertical,
    children:[
    ...
    ]
    )
## Table  (android TableLayout)
    Table(
    //border:TableBorder.all(),
    //columnWidths:{1:FractionColumnWidth(.2)}
    //defaultVerticalAlignment:TableCellVerticalAlignment.top
    //defaultColumnWidth:
        FlexColumnWidth(1.0)
        FractionColumnWidth(.25)
        FixedColumnWidth(30.0)
        IntrinsicColumnWidth()
    children:[
        TableRow(children:{
        WideWidget(),
        MediumWidget(),
        }),
        TableRow(...)
    ]
    )
##SliverAppBar (AppBarLayout AppBar Coordinglayout)
    配合CustomScrollView使用
    SliverAppBar(
        //floating:true 下拉出现上拉隐藏
        expandedHeight:200.0//展开高度
        flexibleSpace:FlexibleSpaceBar(//展开布局
            background:_expandedImage,
        )
    )
    slivers:<Widget>[
    ]
## SliverList  SliverGrid
    SliverList(
    delegate:SliverChildListDelegate([
    widget,
    anotherWidget,
    yetAnotherWidget,])
    //delegate:SliverChildBuilderDelegate(//延迟加载
    //    (BuildContext context,int index){
    //    return aWidget;
    //    })
    )
    
    SliverGrid.count(
    children:scrollItems,
    crowwAxisCount:4,//4列
    )
    SliverGrid.extent(
    crossAxisExtent:90.0//item最大宽度
    )
## FadeInImage
    FadeInImage.assetNetword(//memoryNetword
        //height:300.0
        //fadeInDuration:
        //fadeInCurve:Curves.bounceIn,
        placeholder:'assets/waiting.png',
        image:'https://...'
    )
## StreamBuilder firebase 传感器事件 网络连接状况
    StreamBuilder(
    strean:_myStream,
    builder:(context,snapshot){
    switch(snapshot.connectionState){
    case ConnectionState.waiting:
    case ConnectionState.none:
        return LinearProgressIndicator();
    case ConnectionState.active:
        return MyWidget()
    }
    }
    )
## InheritedModel
    当你想使用上层wiget 的数据时  使用这个玩意


