��ʵ�ʿ����п��ܻ�����һ���������̨��api�ӿڴ����������ݱȽ϶࣬��datatable��ֻ��Ҫ��ʾһ���֡����֮��Ĳ���������Ҫ�õ�û����ʾ�����ݣ�����ֱ����columns�����в�������Ӧ���ֶΣ�������������Դ��ÿһ����6���ֶΣ�

![datatable�õ�������](http://upload-images.jianshu.io/upload_images/3399229-cd7b7a86d4aee24e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

�����ֻ��columns��ֻ����name,position,office����ֻ����ʾ�����
```
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

            }
            ],
```

![ֻ��ʾ��������](http://upload-images.jianshu.io/upload_images/3399229-7aec349000d51194.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

������֮��Ĳ����л��õ�δ��ʾ�����ݣ��������к���ʾ��ϸ��Ϣ����ô����ֻ�������أ�������columnDefs�����и������ص������һ���࣬��hide_column��
```
<style>
        .hide_column{
            display: none;
        }
</style>
```
```
"columnDefs" :
                    [{
                        className: "hide_column",
                        "targets": [2,5] //����3�к͵�6�����أ���0��ʼ����
                    }],
```
�����Ļ���ʹ��datatables��api��õ�ǰ�е����ݵĻ���Ҳ���Ի�õ��������е����ݡ�