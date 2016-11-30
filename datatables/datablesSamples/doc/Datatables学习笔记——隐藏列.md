在实际开发中可能会遇到一种情况，后台的api接口传回来的数据比较多，而datatable中只需要显示一部分。如果之后的操作并不需要用到没有显示的数据，可以直接在columns配置中不配置相应的字段，比如以下数据源中每一项有6个字段：

![datatable拿到的数据](http://upload-images.jianshu.io/upload_images/3399229-cd7b7a86d4aee24e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

如果我只在columns中只配置name,position,office，就只会显示这三项。
```
columns: [{
                "data": "name",
                "orderable": true, // 禁用排序
                "defaultContent": "",
                "width": "10%"

            }, {
                "data": "position",
                "orderable": true, // 禁用排序
                "defaultContent": "",
                "width": "10%"

            }, {
                "data": "office",
                "orderable": false, // 禁用排序
                "defaultContent": "",
                "width": "10%"

            }
            ],
```

![只显示三列数据](http://upload-images.jianshu.io/upload_images/3399229-7aec349000d51194.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

但若是之后的操作中会用到未显示的数据，比如点击行后显示详细信息，那么可以只将其隐藏，可以在columnDefs配置中给想隐藏的列添加一个类，如hide_column。
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
                        "targets": [2,5] //将第3列和第6列隐藏，从0开始计数
                    }],
```
这样的话，使用datatables的api获得当前行的数据的话就也可以获得到隐藏列中的数据。