## 播放暂停音乐
    <div class="audio_btn rotate"><audio loop="" src="images/audio.mp3" id="myAudio"></audio></div>
    //一般情况下，这样就可以自动播放了，但是一些奇葩iPhone机不可以
        document.getElementById('myAudio').play();
        //必须在微信Weixin JSAPI的WeixinJSBridgeReady才能生效
        document.addEventListener("WeixinJSBridgeReady", function () {
            document.getElementById('myAudio').play();
        }, false);
        var flag=true;
        $(".audio_btn").on("click",function(){
            if(flag){
                document.getElementById('myAudio').pause();
                $(this).removeClass('rotate');
                flag=false
            }else{
                flag=true;
                $(this).addClass('rotate');
                document.getElementById('myAudio').play();
            }

        })
