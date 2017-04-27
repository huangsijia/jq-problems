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
    
## 原生transform,原生js动画

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
    
    element.css({
        'transition-timing-function': 'linear',
        'transition-duration': '5000ms',
        'transform': 'translate3d(-' + (width * 2) + 'px,0px,0px)' //设置页面X轴移动
        });
    
## 接口实时加上?t="+new Date().getTime()

    $.ajax({
    url: "href?t="+new Date().getTime()
    })

## tab
    $(".report_menu li").hover(function(){
        var ind = $(this).index();
        $(this).addClass("on").siblings().removeClass("on");
        $(".report_tab li").eq(ind).show().siblings().hide();
    })


## template
    <script src="../../js/artTemplate.js"></script>
    <script id="tp_test" type="text/template">
    {{each data as item}}
    <div class="item">
        <a href="{{item.url}}">
            <div class="report_l1">
                <img src="{{item.img}}" alt="" />
            </div>
            <div class="report_bt"><span>{{item.title}}</span><i></i></div>
        </a>
    </div>
    {{/each}}
    </script>
    <script>
        $(".report_menu li").click(function(){
            var ind = $(this).index(),
                txt = "report" + $(this).text();

            $(this).addClass("on").siblings().removeClass("on");
            $(".report_tab .item").eq(ind).show().siblings().hide();

            getList(txt);
        });

        var reportList = [];

        getList("report2017");

        function getList(txt) {

            if(reportList[txt]){
                darwHtml(reportList[txt])
            }else{
                $.ajax({
                    url:"10.0.1.247:9007/web/about/report.html",
                    data:{"yearType": txt},
                    success:function (json) {
                        darwHtml(json);
                        reportList[txt]=json
                    }
                });
            }

        }
        function darwHtml(json){
            $(".report_tab").html(template('tp_test', json));
        }

    </script>
## 自适应h5
    <meta name="viewport" id="viewport" content="width=320, initial-scale=1, maximum-scale=1, user-scalable=no">
    function isMobile() {
            return /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini|Mobi/i.test(navigator.userAgent) ||
                window.innerWidth < 500;
        }
        function setScale() {
            if (window.top !== window) {
                return;
            }
            var pageScale = 1;

            var width = document.documentElement.clientWidth || 320;
            var height = document.documentElement.clientHeight || 486;

            if (width / height >= 320 / 486) {
                pageScale = height / 486;
            } else {
                pageScale = width / 320;
            }
            // meta
            var content = 'width=320, initial-scale=' + pageScale + ', maximum-scale=' + pageScale + ', user-scalable=no';
            document.getElementById('viewport').setAttribute('content', content);
        }

        if (isMobile()) {
            setScale();
        }
        
##右边菜单滚动

        var lift = $("#lift");
        $.fn.scrollView = function () {
            return this.each(function () {
                $('html, body').animate({
                    scrollTop: $(this).offset().top - $(window).height() / 10 + 92
                }, 1000);
            });
        }

        $("#lift a").click(function () {

            var pid = $(this).attr("data-anchor");
            $(pid).scrollView();
        });

        $(window).scroll(function () {
            var scrollTop = $(document).scrollTop();
            var boxTop = $("#f4").offset().top;
            var contentItems = $(".list"), currentItem;
            if (scrollTop >= boxTop) {
                lift.css({opacity: "1", transform: "scale(1)", visibility: "visible"});
            } else {
                lift.css({opacity: "0", transform: "scale(0)", visibility: "hidden"});
            }

            contentItems.each(function () {
                var contentItem = $(this);
                var offsetTop = contentItem.offset().top;
                if (scrollTop > offsetTop - 200) {
                    currentItem = "#" + contentItem.attr("id");
                }
            });

            if (currentItem && currentItem != lift.find(".curr").attr("data-anchor")) {
                lift.find(".curr").removeClass("curr");
                lift.find("[data-anchor=" + currentItem + "]").addClass("curr");
            }
        });
        
##获取服务器时间

        function getServerTime(){
            $.ajax({
                url:window.location.href.toString(),
                async:false,
                success: function(data, status, xhr) {
                    //console.log(xhr.getResponseHeader("Date"));
                }
            });
            return new Date()
        }
        var serverTime = getServerTime().getTime(),
        time = new Date('2017/05/09 00:00:00').getTime();//当前时间

