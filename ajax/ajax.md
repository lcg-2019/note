### ajax 的函数封装

```javascript
    function ajax(params){
        if(!params){
            alert('没有合适参数');
            return;
        }
        if(!params.url){
            alert('没有url');
            return;
        }
        var obj = {
            method:'GET',
            contType:'text/plain',
            data:null,
            success:function(res){
                console.log(res)
            },
            fail:function(msg){
                console.log(msg)
            }
        }

    params = Object.assign(obj,params);

        var xhr = new XMLRequest();

        xhr.onload = function(){
            var data =JSON.parse(xhr.responseText);
            params.success(data);

        }
        xhr.onerror = function(){
            if(xhr.readystate == 4){
                if(xhr.status == 400){
                 params.fail('400');
   
                }else if(xhr.status == 500){
                 params.fail('500');
   
                }
            }
        }

        xhr.open(params.method,paras.url);
        if(params.data){
            xhr.setRequestHeader('content-type',params.contType)
        }
        xhr.send(paramsdata);
    
    }

```