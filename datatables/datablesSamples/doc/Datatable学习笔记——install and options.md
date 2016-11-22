##1.��װ
�����������ļ�����jQuery�⣬һ��DT�ĺ���js�ļ���һ��DT��css�ļ���ע��jQuery���������DT��js�ļ�֮ǰ��
�����ο��ĵ� http://datatables.club/manual/install.html

```
<!-- ����jQuery -->
<script src="js/jquery-1.11.2.min.js"></script>
<!-- Datables�����ļ� -->
<link href="css/jquery.dataTables.css" rel="stylesheet">
<script src="js/jquery.dataTables.js"></script>
<!-- ���Table -->
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
����ҪӦ��bootstrap��datatables���������datatable��bootstrap��ص�css�ļ���js�ļ���˳��Ϊbootstrap.css��dataTables.bootstrap.css��jQuery.js��jquery.dataTables.js��dataTables.bootstrap.js 

```
<link href="css/bootstrap.min.css" rel="stylesheet">
<script src="js/jquery-1.11.2.min.js"></script>
<script src="js/bootstrap.min.js"></script>
<!-- Datables�����ļ� -->
<link href="css/dataTables.bootstrap.css" rel="stylesheet">
<script src="js/jquery.dataTables.js"></script>
<script src="js/dataTables.bootstrap.js"></script>
```

##2.����
  * ��������
�ٷ��ο��ĵ��� http://datatables.club/reference/option/
```
var sampleTable2 = $('#sample_2').DataTable({
            "lengthMenu": [5, 10, 20, 40],//������ÿҳ��ʾ��¼����select����ʾ��ѡ��
            "searching": true,//�Ƿ��������
            "lengthChange": true,//�Ƿ������û��ı���ÿҳ��ʾ�ļ�¼��
            "paging": true,//��������ҳ
            "processing": true,//�Ƿ���ʾ����״̬(�����ʱ�����ݺܶ�ķ�ʱ�䳤�Ļ���Ҳ����ʾ���)
            "autoWidth": false,//�Ƿ�����Ӧ���
            "deferRender": true,//�ӳ���Ⱦ��������߳�ʼ�����ٶ�
            "stateSave": true, //����״̬ - ��ҳ�����¼��ص�ʱ��ָ�״̬��ҳ�������,���ڵ���ҳˢ��ҳ�棬���Զ�����һҳ
            "dom": '<l<\'#topPlugin\'>f>rt<ip><"clear">',//����DataTables�����Ԫ�ص���ʾ����ʾ˳��
            "ordering": true,//ȫ�ֽ�������
            "serverSide":false,//�Ƿ���������ģʽ
            "ajax": {
                "url": "data/objects_root_array.txt", //��һ��ajax����Դ��ȡ���ݸ��������
                "dataSrc": "" //�������Ի���������ݵķ���
            },
            columns: [{
                "data": "name",
                "orderable": true, // ��������
                "defaultContent": "",
                "width": "10%"

            }, {
                "data": "position",
                "orderable": true, // ��������
                "defaultContent": "",
                "width": "10%"

            }, {
                "data": "office",
                "orderable": false, // ��������
                "defaultContent": "",
                "width": "10%"

            }, {
                "data": "extn",
                "orderable": false, // ��������
                "defaultContent": "",
                "width": "5%"

            }, {
                "data": "salary",
                "orderable": false, // ��������
                "defaultContent": "",
                "width": "10%"

            }, {
                "data": "start_date",
                "orderable": false, // ��������
                "defaultContent": "",
                "width": "10%"

            }
            ],
            "oLanguage": { // ���ʻ�����
                "sProcessing": "���ڻ�ȡ���ݣ����Ժ�...",
                "sLengthMenu": "��ʾ _MENU_ ��",
                "sZeroRecords": "û���ҵ�����",
                "sInfo": "�� _START_ ��  _END_ ����¼ �ܼ�¼��Ϊ _TOTAL_ ��",
                "sInfoEmpty": "��¼��Ϊ0",
                "sInfoFiltered": "(ȫ����¼�� _MAX_ ��)",
                "sInfoPostFix": "",
                "sSearch": "����",
                "sUrl": "",
                "oPaginate": {
                    "sFirst": "��һҳ",
                    "sPrevious": "��һҳ",
                    "sNext": "��һҳ",
                    "sLast": "���һҳ"
                }
            }

        });
```
  * dom
�ٷ��ο��ĵ���
http://datatables.club/reference/option/dom.html
http://datatables.club/manual/daily/2016/05/11/option-dom.html
Datatables�����¶��壺
> 1. `l` ���� length�����Ͻǵĸı�ÿҳ��ʾ�����ؼ�
2. `f` ���� filtering�����ϽǵĹ���������ؼ�
3. `t` ���� table�������
4. `i` ���� info�����½ǵı����Ϣ��ʾ�ؼ�
5. `p` ���� pagination�����½ǵķ�ҳ�ؼ�
6. `r` ���� processing������м�����ݼ��صȴ���ʾ��ؼ�
7. `B` ���� button��Datatables�����ṩ�İ�ť�ؼ���Ĭ����ʾ�����Ͻ�

dom��Ĭ��ֵΪ`lfrtip`�����Ĭ��Ч�����£�

![datatablesĬ�ϵ�domЧ��](http://upload-images.jianshu.io/upload_images/3399229-21d9774d43fc6c2d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
��ֻ����ı����пؼ���λ�ã�����ֱ���������`lfrtip`��˳�򣬵����Ҫ���������������л���Ҫ�����еĻ���������һЩԪ�أ��糣��������һЩ��ť������Ҫͨ�����·�ʽ��
  * `< >` - div elements ����һ��divԪ��?<div><div>
  * `<"#id" >` - div with an id ָ����id��divԪ��?<div id='id'><div>
  * `<"class" >` - div with a class ָ������ʽ����divԪ��?<div class='class'><div>
  * `<"#id.class" >` - div with an id and class ָ����id����ʽ��divԪ��?<div id='id' class='class'><div>

��`"dom": '<"wrapper"flipt>'`����datatables��ʼ����Ľṹ���£�
```
<div class="wrapper">
      {filter}
      {length}
      {information}
      {pagination}
      {table}
    </div>
```
��`"dom": '<"top"i>rt<"bottom"flp><"clear">'`����datatables��ʼ����Ľṹ���£�
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
��Ҫ�ڱ���������button�����Խ�dom��ֵ��Ϊ`"dom": '<l<\'#topPlugin\'>f>rt<ip><"clear">'`��Ȼ���������м�`��initComplete����initButton`��initButton��һ��������ʵ������������������button����
```
function initButton(data) {
                var topPlugin = '<button class="btn btn-primary btn-sm float-r"><i class="fa fa-plus"></i>?�� ��</button>';
                $("#topPlugin").append(topPlugin);//�ڱ���Ϸ�topPlugin DIV��׷��HTML
            }
```
  * Ĭ�����ã�Setting defaults��
Ĭ�������޸ĺ��Ӧ�õ����еı���У������ȼ�����ڽ��б���ʼ��ʱ��������ò�����
ʹ�����·����޸�Ĭ�����ã�
```
//����DataTablesĬ�ϲ���
 $.extend(true, $.fn.dataTable.defaults, {
 "language": {
 "url": "/assets/Chinese.txt"
 },
 "dom": "<'row'<'col-md-6'l<'#toolbar'>><'col-md-6'f>r>" +
 "t" +
 "<'row'<'col-md-5 sm-center'i><'col-md-7 text-right sm-center'p>>"
 });
```