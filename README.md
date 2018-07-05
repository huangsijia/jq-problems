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
        (function() {
            var videoPlay = document.getElementById("video"),
                partStart = document.getElementById("partStart"),
                partVideo = $(".partVideo"),
                partLink = $(".partLink");

            partStart.addEventListener('touchstart', function() {
                $(".partStart").hide();
                partVideo.show();
                videoPlay.play();
            });

            videoPlay.onended = function() {
                partVideo.hide();
                partLink.show();
            };
        })()
        
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
        
## 右边菜单滚动

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
        
## 获取服务器时间

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
        
## 绑定服务器的时间
       result._serviceDate = new Date(arguments[2].getResponseHeader("Date"))
##  题目

    1、eval是做什么的？有什么类似的api吗？
    它的功能是把对应的字符串解析成JS代码并运行；
    应该避免使用eval，不安全，非常耗性能（2次，一次解析成js语句，一次执行）。
    由JSON字符串转换为JSON对象的时候可以用eval，var obj =eval('('+ str +')');

    2、“===”和”==”有什么区别
    =会做类型转换  ===强等于 

    3、	'' == '0' // false 
    0 == '' // true 
    0 == '0' // true 
    false == 'false' // false 
    false == '0' // true 
    false == undefined // false 
    false == null // false 
    null == undefined // true 
    ' \t\r\n ' == 0 // true

    4、写出下面JavaScript代码输出的内容
    var arr = [1, 2, 3];
    for (var i = 0, j; j = arr[++i];) {
      console.log(j);
    }
    console.log(i);
    console.log(j);
    //2,3,3，undefined 

    5、用css+html实现下面的图形
    width:0;height:0;border-bottom:10px;
## 转码
    encodeURIComponent
## 身份证，姓名，电话
    Vue.filter('formatIdCart',function(value){
      var length = value.length - 4;
      var temp = "";
      for(var i = 0; i < length; i++){
        if(i % 4 == 0){
          console.log(i);
          temp += " *";
        }else{
          temp += "*";
        }
      }
      var last =  value.substr(length, length+4);
      return temp + last;
    })
function name(value){
            var len = value.length;
            var symbol = value.slice(1, len).length;
            var str = "";
            for (var i = 0; i < symbol; i++) {
                str += "*";
            }
            return value.replace(value.slice(1, len), str);
        }
        function mobile(value){
            value = value.toString();
            if (value && value.length == 11) {
                return value.substr(0, 3) + " **** " + value.substr(7, 11);
            }
        }
    
## 表单验证用户名，身份证，银行卡
    var regName = /^[\u4e00-\u9fa5]{2,6}$/;
    var regIdCard = /(^\d{15}$)|(^\d{18}$)|(^\d{17}(\d|X|x)$)/;
    var regBank = /^[0-9]{16,19}$/;
    var regMobile = /^(((1[3456789][0-9]{1})|(15[0-9]{1}))+\d{8})$/;
## 时间戳
    timeStamp
    new Date().getTime()
    
## input不输入空格
     @input="keyFun" onkeyPress="var keyCode = event.keyCode;if ((keyCode >= 48 && keyCode <= 57)){event.returnValue = true;} else {event.returnValue = false;}"

## 只显示10条数据
    u = navigator.userAgent; // 排名
    if(!!u.match(/AppleWebKit.*Mobile.*/) && !!u.match(/AppleWebKit/)){
        json.list= json.list.slice(0,10);
    }
    
## $.unique() 函数用于对DOM元素数组进行排序，并移除重复的元素。
    注意：1. 仅适用于DOM元素数组，不能处理字符串或者数字数组。
    2. 这里的重复指的是两个元素实际上是同一个元素(通过全等"==="来判断)，例如不同节点属性相同的元素不被认为重复的元素。 
    3. 在jQuery 3.0中，这种方法已被弃用，只是jQuery.uniqueSort()的别名。请使用该方法代替。
    
## 1.排序；2.替换匹配字符串
    1.[1,3,5,10].sort((a,b)=>a-b)
    2."bob".replace(/b/g,"c")==="coc"
    

## 2000>>2,000.00
    function fmoney (s, n) {
      n = n > 0 && n <= 20 ? n : 2
      s = parseFloat((s + '').replace(/[^\d\.-]/g, '')).toFixed(n) + ''
      var l = s.split('.')[0].split('').reverse()
      var r = s.split('.')[1]
      var t = ''
      for (var i = 0; i < l.length; i++) {
        t += l[i] + ((i + 1) % 3 === 0 && (i + 1) !== l.length ? ',' : '')
      }
      return t.split('').reverse().join('') + '.' + r
    }
    
## 手机浏览器返回没有加载js
    window.onpageshow = function (e) {
     if (e.persisted) {
           window.location.reload(true)
     } 
    }

    
## json互转
    JSON.parse
    JSON.stringify
    
## 正则字符串
    new RegExp("^1[3|4|5|7|8][0-9]{9}$")时不能有斜杠/
## 字符串转number
    Number("123")
## chrome form用js去submit,无效提示Form submission canceled because the form is not connected
    解决方案$(document.body).append(form);
## 一万亿以内的人民币小写转大写，暂不考虑连续零的处理
    function moneyCaseConvert(num){
        var upperArr=["零","壹","贰","叁","肆","伍","陆","柒","捌","玖"],
            levelArr=["","拾","佰","仟","万","拾","佰","仟","亿","拾","佰","仟","万"],
            numArr=num.toString().split("").reverse(),
            result=[];
        for(var i=numArr.length-1;i>=0;i--)
            result.push(upperArr[numArr[i]]+levelArr[i]);
        return result.join("");
    }

    //Test
    console.log(CaseConversion(1234567891234));
    //壹万贰仟叁佰肆拾伍亿陆仟柒佰捌拾玖万壹仟贰佰叁拾肆
    
## 整数转为千分位记数法
    function numFormat(val){
        var numStr = val.toString(),
            length = numStr.length,
            extra = length % 3,
            count = (length - extra)/3,
            result = numStr.substr(0,extra);
        for(var i = 0; i < count; i++){
            result += "," + numStr.substr(extra+i * 3,3); 
        }
        return result.replace(/^,/,"");
    }    
    console.log(numFormat(123456789));//123,456,789
## 正则
    function numberFormat(val){
    var numArr=String(val).split(".");
    numArr[0] = numArr[0].replace(new RegExp("(\\d)(?=(\\d{3})+$)","ig"),"$1,");
    return numArr.join(".");
    }
## 禁止页面被iframe
    http://www.jb51.net/article/56889.htm
    https://developer.mozilla.org/zh-CN/docs/Web/HTTP/X-Frame-Options
    
## 页面加载不出来
    $(document).on("click",".submit", function () {})
## 复制
    <p class="txt">BXJR2017HSB513</p>
    <textarea style="width:0;height:0" cols="20" rows="10" class="copy">BXJR2017HSB514</textarea>
    <a class="btn">点击复制</a>
    <script>
        $(".btn ").on("click ", function() {
            var txt = $(".copy");
            txt.select(); // 选择对象
            document.execCommand("Copy"); // 执行浏览器复制命令
            alert("已复制好，可贴粘。");
        })
    </script>
    
## 防止页面被框架包含
    if(top.location != self.location && ".baidu.com/".indexOf(top.location.href) == -1){
        top.location = self.location;//防止页面被框架包含
    }
## 只允许输入俩位小数
    $(this).val($(this).val().replace(/([0-9]+\.[0-9]{2})[0-9]*/,"$1"));
    this.amount = this.amount.replace(/([0-9]+\.[0-9]{2})[0-9]*/,"$1");
## 只允许输入数字
    onkeyPress="var keyCode = event.keyCode;if ((keyCode >= 48 && keyCode <= 57) || keyCode == 46){event.returnValue = true;}else {event.returnValue = false;}"

## location
 var whichTab = location.pathname.split('/'),nowTab = whichTab[whichTab.length-1];
 
## 并发双接口
    $.when(
    $.getJSON('${resource(file: 'assets/mobile/js/success.json')}'),
    $.getJSON('${resource(file: '/secure/get-login-info.html')}')
    ).then(function(a,b){
        var json=a[0],data=b[0]
        json.username=data.username;
        json.mobile=data.mobile;
        var success = template('success', json);
        $('.gold-success').html(success);
    });
## tab取值
    e.currentTarget.dataset.tab
## 后台返回含标签修改为文案
    $(".gold-mall-bottom").html($('<div>').html(res.commodityVO.synopsis).text());
## 滚动到顶部固定
var tabTop = $(".gold-mall-tab").offset().top;
    $(window).scroll(function(){
        var nowTop =  $(this).scrollTop();
        if(tabTop<=nowTop){
            $(".gold-mall-tab").addClass("fixed");
        }else{
            $(".gold-mall-tab").removeClass("fixed");
        }
    })
## 屏蔽emoji
    $("input").on('input',function(){    
        this.value = this.value.replace(/\uD83C[\uDF00-\uDFFF]|\uD83D[\uDC00-\uDE4F]/g, "");
    })
    
## 调试
    <script src="//cdn.bootcss.com/eruda/1.3.0/eruda.min.js"></script>
    <script>eruda.init();</script>

## 移动
touchstart(e) {
            if (this.touchFlag) {
                e.stopPropagation();
            }
        },
        touchmove(e) {
            var current_touchmoveTop = $(".pullData").offset().top;
            if (
                this.touchmoveLastTop == current_touchmoveTop &&
                current_touchmoveTop > 0
            ) {
                this.touchFlag = false;
            } else {
                this.touchFlag = true;
            }
            this.touchmoveLastTop = current_touchmoveTop;
        },
        
## 上拉 下翻
<div v-html="pullData" class="pullData" @touchstart='touchstart($event)'  @touchmove="touchmove($event)"></div>
touchFlag: true, // touchstart 阻止冒泡的开关
                swiperOption: {
                    direction: "vertical",
                    on: {
                        slideChange() {
                            if (this.activeIndex === 0) {
                                $(".detail").css("paddingBottom", 0);
                                self.touchFlag = true;
                                self.firstInset = true;
                            } else {
                                $(".detail").css( "paddingBottom", $(".pullData").height() - $(window).height() + 150 );
                                
                            }
                        }
                    }
                },
                startY: 0,
                endY: 0,
                backTop:false,
                firstInset:true,
touchstart(e) {
        //翻到第二页，没有下拉
        if(window.pageYOffset == 0 && this.firstInset){
            this.touchFlag=false;
        }
        //翻到第二页，下拉之后
        if(window.pageYOffset == 0 && this.backTop){
            this.touchFlag=false;
        }
        if (this.touchFlag) {
            e.stopPropagation();
        }
        this.startY = e.touches[0].clientY;
    },
    touchmove(e) {
        if(window.pageYOffset == 0){
            this.touchFlag=false;
        }else{
            this.touchFlag=true;
        }
        this.endY = e.touches[0].clientY;
        if(this.endY<this.startY){// 向下
            this.touchFlag=true;
            this.firstInset=false;
        }else{
            this.backTop=true;// 向下
        }
        if (this.touchFlag) {
            e.stopPropagation();
        }

    },
## 滚动加载
parameter: {
        offset: 0,
        max:10,
    },
    loadEnd: false,
    initLock: true,
    hasNext: true,//没有数据了，不用继续往下
        loadMore() {
        //上拉加载更多
        if (this.initLock) {
            return;
        }
        if (!this.hasNext) {
            return;
        }
        if(this.loading){
            return
        }
        this.loading = true;
        this.$public.API_GET({
            url: "a",
            data: this.parameter,
            success: result => {
                for(var item in result.data){
                    this.list.push(result.data[item])
                }
                this.parameter.offset += this.parameter.max;
                this.loading = false;
                if (result.data.length < this.parameter.max) {
                    this.hasNext = false;
                }
            }
        });
        },
        initDataFun(finishFun) {
        //初始化信息&&下拉刷新
        this.parameter.offset = 0;
        this.parameter.max = 10;
        this.hasNext=true;
        this.list=[];
        this.loadEnd=false;
        this.$public.API_GET({
            url: "a",
            data: this.parameter,
            success: result => {
                this.loadEnd = true;
                this.list = result.data;
                this.parameter.offset += this.parameter.max;
                if (result.data.length < this.parameter.max) {
                    this.hasNext = false;
                }
                this.initLock = false;
                //下拉刷新释放函数
                if (typeof finishFun == "function") {
                    finishFun();
                }
            }
        });
        },
## 转码
encodeURIComponent

## 绑定服务器的时间.replace(/\-/g,'/')
var _date = xhr.getResponseHeader("Date");
// 绑定服务器的时间
if (_date) {
    playoffs = new Date(_date).getTime();
} else {
    playoffs = new Date().getTime();
}
## 回车键事件
    $(document).keypress(function(e) {
        if(e.which == 13) {}
     }
## 输入框文字变化时执行以下代码
    $("#picker-filter").bind('input propertychange',function () {
