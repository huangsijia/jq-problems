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
        
        
        /*音乐*/
        var audio = $('#car_audio');
        var isPlaying = false;
        function playAudio() {
            var audio = $('#car_audio');
            if (audio.attr('src') == undefined) {
                audio.attr('src', audio.data('src'));
            }
            audio[0].play();
            isPlaying = true;
        }
        $(function(){
            playAudio();
            document.addEventListener("WeixinJSBridgeReady", function () {
                WeixinJSBridge.invoke('getNetworkType', {}, function (e) {
                    network = e.err_msg.split(":")[1];  //结果在这里
                    playAudio();
                });
            }, false);
        })
        
        
## 加载多个ajax
    $.when(
        $.getJSON('aa.html'),
        $.getJSON('bb.html')
    ).then(function(a, b) {  // 或者也可以使用 ".done"}
        //奖品数据
        加载多个ajax
        
## 自执行
    <div class="win-out">
        <div class="win on" style="top: 17.1287%;"><div class="win-con">恭喜 <span>132****0011</span> 获得 AIRWEAR防雾霾口罩</div></div>
    </div>
    .win{width:100%;position:absolute;left:100%;z-index:999;font-size:1.1rem;transition:all 10s;}
    .win .win-con{height:3rem;line-height:3rem;border-radius:3rem;background:rgba(48,5,0,.6);padding:0 40px;color:#fff;display:inline-block;}
    .win.on{left:-200%;}
    <sript>
    setTimeout(function () {
        winAnimation($(".win-out"));
    }, 100)
     function winAnimation(obj) {
        var first = obj.find(".win").eq(0);
        animateNext(first);
        function animateNext(first) {
            var now = first,range = 20 * Math.random();
            now.css({top: range + "%"}).addClass("on");
            setTimeout(function () {
                now = now.next();
                if(now){
                    animateNext(now);
                }
            }, 4000);
        }
    }
    </script>
    
##原生transform

    var cycle = window.document.getElementById("cycle")
    var deg = self.$("#cycle").css("-webkit-transform")
    //App.showToast("deg   " )
    deg = deg.substring(7, deg.length - 4)
    var mathDeg = parseInt(deg)
    cycle.style.webkitTransform = "rotate(" + (mathDeg + key * 45) + "deg)";
    cycle.style.MozTransform = "rotate(" + (mathDeg + key * 45) + "deg)";
    cycle.style.msTransform = "rotate(" + (mathDeg + key * 45) + "deg)";
    cycle.style.OTransform = "rotate(" + (mathDeg + key * 45) + "deg)";
    cycle.style.transform = "rotate(" + (mathDeg + key * 45) + "deg)";
    
接口实时加上?t="+new Date().getTime()

    $.ajax({
    url: "href?t="+new Date().getTime()
    })
