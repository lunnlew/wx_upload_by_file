# wx_upload_by_file
基于input file的图片上传demo
```
<img id="image_2_image"/>
<input  type="file" accept="image/*" capture="camera" class="filebox" name="image_2" id="image_2" />
<input type="hidden" name="image_2_url" value="" id="image_2_url" />
```
```
var UPLOAD_URL = './index.php?i=1&j=1&c=utility&a=upload&do=upload&type=image';
var u1 = new UploadPic();
    u1.init({
        selector: '#image_2',
        callback: function(base64,input,u) {
            $.ajax({
                url: UPLOAD_URL,
                data: { file: base64, gtype: 'image', ctype: 'local', 'base64':'base64','oriName':u.fileName},
                type: 'post',
                dataType: 'json',
                success: function(i) {
                    input.prev().prev().remove();
                    input.prev().attr('src',i.url).css('display','block');;
                    input.next().val(i.key);
                    //jq.show_tip('上传成功!');
                }
            })
        },
        loading: function() {
            //jq.show_tip('上传中!');
        }
    });
    ```
