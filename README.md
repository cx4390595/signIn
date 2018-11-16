       /*日期签到*/
        function time(YYYY, MM) {
            var today = new Date();
            var tindex, exist;
            var date = new Date(YYYY + '/' + (MM + 1) + '/1 00:00:00');
            var lastDate = new Date(date - 3600000 * 24).getDate();
            var length = lastDate;
            var dateWeek = date
            /*标题月份*/
            $(".signIn_main .title span").text(MM+"月")
            $(".signIn_main .pop span").text(lastDate)
            dateWeek.setMonth(date.getMonth() - 1)

            var oLi = "";

            console.log(new Date(today.getFullYear() + '/' + (today.getMonth() + 1) + '/' + today.getDate()), date)
            if(today.getFullYear() === YYYY && today.getMonth() + 1 === MM) exist = true;
            for (var i = 0; i < length; i++) {
                if(exist && today.getDate() === i + 1) tindex = i;
                oLi += "<li>" + (i + 1) + "</li>";
            }
            // console.log(tindex)
            $(".month").append(oLi);

            function liNum(num) {
                var aLi = ""
                for (var i = 0; i < num; i++) {
                    aLi += "<li></li>"
                }
                return aLi
            }

            var aLi = ""
            var item = 42 - length - dateWeek.getDay();
            for (var i = 0; i < item; i++) {
                aLi += "<li></li>";
            }
            $('.month').prepend(liNum(dateWeek.getDay()));
            $('.month').append(aLi)

            $('.btn_signMe').on("click",function () {
                if(typeof tindex !== 'undefined' && $("li").eq(tindex).hasClass("")){
                    $('.cont .month li').eq(dateWeek.getDay()+tindex).addClass("onOff")
                }

            })
        }
        time(2018, 9)//必须改成系统时间的当前月份才能生效