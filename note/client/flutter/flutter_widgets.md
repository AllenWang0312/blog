
## SafeArea

## Expanded 
    ʹcolum �� row ��ĳ���������ʣ��ռ�
    ���� android:weight

## Wrap

## AnimatedContainer 
    ��������
    ͨ��setState() �ı�ĳ������ֵ ���Զ�Ϊ����Ӷ���

## Opacity (��͸����)  Visibility=GONE
    Opacity(
        opacity:0.0,
        child:MyWidget(Colors.blue),
    )
## FutureBuilder 
    �첽ִ������ ���ݴ�������ʾ����   

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
    
    �� flutter_lms/lib/common/my_fade_in.dart
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
    ���CustomScrollViewʹ��
    SliverAppBar(
        //floating:true ����������������
        expandedHeight:200.0//չ���߶�
        flexibleSpace:FlexibleSpaceBar(//չ������
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
    //delegate:SliverChildBuilderDelegate(//�ӳټ���
    //    (BuildContext context,int index){
    //    return aWidget;
    //    })
    )
    
    SliverGrid.count(
    children:scrollItems,
    crowwAxisCount:4,//4��
    )
    SliverGrid.extent(
    crossAxisExtent:90.0//item�����
    )
## FadeInImage
    FadeInImage.assetNetword(//memoryNetword
        //height:300.0
        //fadeInDuration:
        //fadeInCurve:Curves.bounceIn,
        placeholder:'assets/waiting.png',
        image:'https://...'
    )
## StreamBuilder firebase �������¼� ��������״��
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
    ������ʹ���ϲ�wiget ������ʱ  ʹ���������


