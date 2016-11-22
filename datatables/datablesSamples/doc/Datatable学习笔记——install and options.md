##1.安装
需引入三个文件，即jQuery库，一个DT的核心js文件和一个DT的css文件，注意jQuery库的引用在DT的js文件之前。
官网参考文档 http://datatables.club/manual/install.html

```
<!-- 引入jQuery -->
<script src="js/jquery-1.11.2.min.js"></script>
<!-- Datables引入文件 -->
<link href="css/jquery.dataTables.css" rel="stylesheet">
<script src="js/jquery.dataTables.js"></script>
<!-- 添加Table -->
<table id="sample_1">    
  <thead>       
    <tr>           
      <th>Name</th>            
      <th>age</th>        
    </tr>    
  </thead>    
  <tr>        
    <td>Joe</td>        
    <td>18</td>    
  </tr>    
  <tr>        
    <td>Grace</td>        
    <td>16</td>    
  </tr>
</table>
<script>   
   var mytable = $('#sample_1').DataTable();
</script>
```
若需要应用bootstrap到datatables则可以引入datatable中bootstrap相关的css文件和js文件，顺序为bootstrap.css、dataTables.bootstrap.css、jQuery.js、jquery.dataTables.js、dataTables.bootstrap.js 

```
<link href="css/bootstrap.min.css" rel="stylesheet">
<script src="js/jquery-1.11.2.min.js"></script>
<script src="js/bootstrap.min.js"></script>
<!-- Datables引入文件 -->
<link href="css/dataTables.bootstrap.css" rel="stylesheet">
<script src="js/jquery.dataTables.js"></script>
<script src="js/dataTables.bootstrap.js"></script>
```

##2.配置
  * 常用配置
官方参考文档： http://datatables.club/reference/option/
```
var sampleTable2 = $('#sample_2').DataTable({
            "lengthMenu": [5, 10, 20, 40],//定义在每页显示记录数的select中显示的选项
            "searching": true,//是否禁用搜索
            "lengthChange": true,//是否允许用户改变表格每页显示的记录数
            "paging": true,//开启表格分页
            "processing": true,//是否显示处理状态(排序的时候，数据很多耗费时间长的话，也会显示这个)
            "autoWidth": false,//是否自适应宽度
            "deferRender": true,//延迟渲染，可以提高初始化的速度
            "stateSave": true, //保存状态 - 在页面重新加载的时候恢复状态（页码等内容,如在第三页刷新页面，会自动到第一页
            "dom": '<l<\'#topPlugin\'>f>rt<ip><"clear">',//定义DataTables的组件元素的显示和显示顺序
            "ordering": true,//全局禁用排序
            "serverSide":false,//是否开启服务器模式
            "ajax": {
                "url": "data/objects_root_array.txt", //从一个ajax数据源读取数据给表格内容
                "dataSrc": "" //数据属性或操作表数据的方法
            },
            columns: [{
                "data": "name",
                "orderable": true, // 启用排序
                "defaultContent": "",
                "width": "10%"

            }, {
                "data": "position",
                "orderable": true, // 启用排序
                "defaultContent": "",
                "width": "10%"

            }, {
                "data": "office",
                "orderable": false, // 禁用排序
                "defaultContent": "",
                "width": "10%"

            }, {
                "data": "extn",
                "orderable": false, // 禁用排序
                "defaultContent": "",
                "width": "5%"

            }, {
                "data": "salary",
                "orderable": false, // 禁用排序
                "defaultContent": "",
                "width": "10%"

            }, {
                "data": "start_date",
                "orderable": false, // 禁用排序
                "defaultContent": "",
                "width": "10%"

            }
            ],
            "oLanguage": { // 国际化配置
                "sProcessing": "正在获取数据，请稍后...",
                "sLengthMenu": "显示 _MENU_ 条",
                "sZeroRecords": "没有找到数据",
                "sInfo": "从 _START_ 到  _END_ 条记录 总记录数为 _TOTAL_ 条",
                "sInfoEmpty": "记录数为0",
                "sInfoFiltered": "(全部记录数 _MAX_ 条)",
                "sInfoPostFix": "",
                "sSearch": "搜索",
                "sUrl": "",
                "oPaginate": {
                    "sFirst": "第一页",
                    "sPrevious": "上一页",
                    "sNext": "下一页",
                    "sLast": "最后一页"
                }
            }

        });
```
  * dom
官方参考文档：
http://datatables.club/reference/option/dom.html
http://datatables.club/manual/daily/2016/05/11/option-dom.html
Datatables有以下定义：
> 1. `l` 代表 length，左上角的改变每页显示条数控件
2. `f` 代表 filtering，右上角的过滤搜索框控件
3. `t` 代表 table，表格本身
4. `i` 代表 info，左下角的表格信息显示控件
5. `p` 代表 pagination，右下角的分页控件
6. `r` 代表 processing，表格中间的数据加载等待提示框控件
7. `B` 代表 button，Datatables可以提供的按钮控件，默认显示在左上角

dom的默认值为`lfrtip`，因此默认效果如下：

![datatables默认的dom效果](http://upload-images.jianshu.io/upload_images/3399229-21d9774d43fc6c2d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
若只是想改变现有控件的位置，可以直接重新组合`lfrtip`的顺序，但如果要对其做更灵活的排列或者要在现有的基础上增加一些元素，如常见的增加一些按钮，则需要通过以下方式：
  * `< >` - div elements 代表一个div元素?<div><div>
  * `<"#id" >` - div with an id 指定了id的div元素?<div id='id'><div>
  * `<"class" >` - div with a class 指定了样式名的div元素?<div class='class'><div>
  * `<"#id.class" >` - div with an id and class 指定了id和样式的div元素?<div id='id' class='class'><div>

如`"dom": '<"wrapper"flipt>'`，则datatables初始化后的结构如下：
```
<div class="wrapper">
      {filter}
      {length}
      {information}
      {pagination}
      {table}
    </div>
```
如`"dom": '<"top"i>rt<"bottom"flp><"clear">'`，则datatables初始化后的结构如下：
```
<div class="top">
      {information}
    </div>
    {processing}
    {table}
    <div class="bottom">
      {filter}
      {length}
      {pagination}
    </div>
    <div class="clear"></div>
```
若要在表格上面添加button，可以将dom的值赋为`"dom": '<l<\'#topPlugin\'>f>rt<ip><"clear">'`，然后在配置中加`“initComplete”：initButton`，initButton是一个函数，实现这个函数在其中添加button，如
```
function initButton(data) {
                var topPlugin = '<button class="btn btn-primary btn-sm float-r"><i class="fa fa-plus"></i>?新 增</button>';
                $("#topPlugin").append(topPlugin);//在表格上方topPlugin DIV中追加HTML
            }
```
  * 默认配置（Setting defaults）
默认配置修改后会应用到所有的表格中，但优先级会低于进行表格初始化时传入的配置参数。
使用以下方法修改默认配置：
```
//配置DataTables默认参数
 $.extend(true, $.fn.dataTable.defaults, {
 "language": {
 "url": "/assets/Chinese.txt"
 },
 "dom": "<'row'<'col-md-6'l<'#toolbar'>><'col-md-6'f>r>" +
 "t" +
 "<'row'<'col-md-5 sm-center'i><'col-md-7 text-right sm-center'p>>"
 });
```