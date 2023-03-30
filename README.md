# js-by-window
js飘窗，碰到边缘反弹



<div id="cloud2" class="cloud2" style="top: 751px; right: 47px;">


        <a target="_blank" href="跳转地址"><img src="/${res}/images/piao.png"
                style="width:300px;float: right;"></a>

        <div class="cloud2_close" onclick="javascript:document.getElementById('cloud2').style.display='none';">关闭</div>
    </div>
    <style>
        * {
            margin: 0;
            padding: 0;
            font-family: "微软雅黑";
        }

        .cloud2 {
            position: fixed;

            z-index: 999;
            background-color: #ddd;
            background: none;
        }

        .cloud2 a {
            display: block;
        }

        .cloud2 a img {
            display: block;
            max-width: 350px;
            height: auto;

        }

        .cloud2_close {
            width: 40px;
            height: 25px;
            position: absolute;
            bottom: -20px;
            right: 0px;
            font-size: 13px;
            line-height: 25px;
            color: #333;
            text-align: center;
            cursor: pointer;
            font-family: "微软雅黑";
            text-align: right;
        }

        .test {
            width: 300px;
            height: 200px;
            position: fixed;
            top: 0px;
            left: 0px;
            background-color: #0f0;
        }
    </style>
    <script>
        $(document).ready(function () {

            var f_speed = 20;
            var fi_top = 50,
                fi_right = 0;
            var $f_cloud2 = $("#cloud2");
            //var $f_cloud = $(".test");

            var f_top = 0,
                f_right = 0;
            var f_W = $(window).width() - $f_cloud2.width();
            var f_H = $(window).height() - $f_cloud2.height();

            function f_auto() {
                if (fi_top >= 0 && fi_top < f_H) {
                    fi_top++;
                    f_top = 1 * fi_top;
                } else if (fi_top >= f_H && fi_top < 2 * f_H) {
                    fi_top++;
                    f_top = 2 * f_H - fi_top;
                } else {
                    fi_top = 0;
                    fi_top++;
                    f_top = 1 * fi_top;
                }
                if (fi_right >= 0 && fi_right < f_W) {
                    fi_right++;
                    f_right = 1 * fi_right;
                } else if (fi_right >= f_W && fi_right < 2 * f_W) {
                    fi_right++;
                    f_right = 2 * f_W - fi_right;
                } else {
                    fi_right = 0;
                    fi_right++;
                    f_right = 1 * fi_right;
                }
                $f_cloud2.css({
                    top: f_top,
                    right: f_right
                });
            }
            var f_cloud2 = setInterval(f_auto, f_speed);
            f_auto();

            $f_cloud2.hover(function () {
                clearInterval(f_cloud2);
            }, function () {
                f_cloud2 = setInterval(f_auto, f_speed);
            });

            $(window).resize(function () {
                f_W = $(window).width() - $f_cloud2.width();
                f_H = $(window).height() - $f_cloud2.height();
                f_auto();
            });
        });
    </script>
