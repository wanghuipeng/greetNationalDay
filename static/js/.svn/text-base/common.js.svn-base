var IMAGE_FILE_URL="http://img.youlanw.com/";
$(function(){
	
	/*app内嵌页面 面试快 底部高度补长*/
	function footer_height_supply_sty(){$('.b-fixed').height($('.b-fixed ul').height());}
	footer_height_supply_sty();
	$(window).resize(function(){
		footer_height_supply_sty();
	});
	
	//回车搜索
	document.onkeydown = function (e) {
		var theEvent = window.event || e;
		var code = theEvent.keyCode || theEvent.which;
		if (code == 13) {
			$(".search-enter").click();
		}
	};
	
	if($("img").hasClass("pic-center")){
		$("body").css("background-color","#fff");
	}
	//create mask-layer
	$('body').append('<div class="mask-layer"></div>');
	//nav-panel
	$('.icon-menu').click(function(){
		$('.mask-layer').show();
		$('.nav-panel').addClass('on');
		$(this).addClass('active');
	});
	$('.mask-layer').click(function(){$('.nav-panel').removeClass('on');$('.mask-layer').hide();$('.icon-menu').removeClass('active');});
	//为职位信息等列表单条记录添加触摸点击事件
	$(".joblist-each").click(function(){$(this).addClass('active-g');});
	//close quick-signup
	$('.icon-close').click(function(){
		Cookie.setCookie("close_date","hide",7);
		$('.quick-signup').hide();
	});
	//select
	var m_select_result='';
	$('.m-select-wrapper li,.m-select-wrapper .form-g-each-r,.m-select-wrapper .form-g-text-2,.m-select-trigger').click(function(){
		$('body').append('<div class="mask-layer-2"></div>');
		$('.mask-layer-2').show();
		$('#'+$(this).data('role')).addClass('on');
		$(this).find('.arrow-d-2').addClass('on');
		$(this).siblings().find('.arrow-d-2').removeClass('on');
		$(this).addClass($(this).data('role'));
		if($('#'+$(this).data('role')).height()>$(window).height()){
			$('#'+$(this).data('role')).height($(window).height());
		}
	});
	$('.m-select-wrapper2 .form-g-each-r').click(function(){
		$(this).find('.arrow-d-2').addClass('on');
		$('body').append('<div class="mask-layer-2"></div>');
		$('.mask-layer-2').show();
		$('#'+$(this).data('role')).addClass('on');
		$(this).addClass($(this).data('role'));
		var current_text=$(this).find('.form-g-text').text();
		$('#'+$(this).data('role')+' .m-selected2').text(current_text);//给已选择初始化
		$('#'+$(this).data('role')+' ul li').each(function(){
			if($(this).text()==current_text){
				$(this).addClass('current').siblings().removeClass('current');//
			}
		});
		$('#'+$(this).data('role')+' .m-select-list2.hold li').removeClass('active');
		$('#'+$(this).data('role')+' .m-selected2').html('请选择期望工作');
		to_append_content='';
		var height_remain=$(window).height()-100;
		if($('.m-select-list2').height()>=height_remain){$('#wrapper').height(height_remain)}
	});
	$('.m-select-list .m-select-title').click(function(){
		$('.m-select-wrapper li').find('.arrow-d-2').removeClass('on');
		$('.m-select').removeClass('on');
		$('.mask-layer-2').remove();
		$('.'+$(this).parent().parent().attr('id')+' span').text($('.'+$(this).parent().parent().attr('id')+' span').data('default'));//select title点击时，给其对应的select初始化
		$(this).addClass('current').siblings().removeClass('current');
		$('.'+$(this).parents('.m-select').attr('id')+' .out-input').text($('.'+$(this).parents('.m-select').attr('id')+' .out-input').data('default'));
	});
	$('.m-select-title2 .close').click(function(){
		$('.arrow-d-2').removeClass('on');
		$('.m-select').removeClass('on');
		$('.mask-layer-2').remove();
		$('.'+$(this).parent().parent().attr('id')+' span').text($(this).parents('.m-select').find('.m-selected2').text());//取值
	});
	$('.m-select-list li,.m-select-r li').not('.m-select-title').not('.hold li').click(function(){
		$('.arrow-d-2').removeClass('on');
		$('.m-select').removeClass('on');
		$('.mask-layer-2').remove();
		$('.'+$(this).parent().parent().attr('id')+' span').text($(this).text());//取值
		$(this).addClass('current').siblings().removeClass('current');
		m_select_result=$(this).text();
		$('.'+$(this).parents('.m-select').attr('id')+' .out-input').text(m_select_result);
	});
	
	$('.m-select-list2').not('.hold').find('li').click(function(){
		$(this).parents('.m-select').find('.m-selected2').text($(this).text());
	});
	
	//要追加到已选择区域的内容
	var to_append_content='';
	$('.m-select-list2.hold li').click(function(){
		if ($('.active').length<5){
			if(!($(this).hasClass('active'))){
				to_append_content+='<span class="tag">'+$(this).text()+'</span>'+' ';
				$(this).parents('.m-select').find('.m-selected2').html('').html(to_append_content);
				$(this).addClass('active');//标记是否已添加
			}
		} 
	});
	
	//允许删除已选择的条件
	$('.m-selected2').on('click','.tag',function(){
		var tag_this=$(this);
		to_append_content='';
		$(tag_this).parents('.m-select').find('.m-select-list2.hold li').each(function(){
			if($(this).text()==tag_this.text()){
				$(this).removeClass('active');//移除某个选择项的时候，对应地清掉已选择标志
			}
			if($(this).hasClass('active')){
				to_append_content+=''+'<span class="tag">'+$(this).text()+'</span>'+' '
				$(this).parents('.m-select').find('.m-selected2').html(to_append_content);
			}
		});
		if($(this).parents('.m-selected2').find('.tag').length==1){
			$(this).parents('.m-selected2').text('请选择期望工作');
		}
		$(this).remove();//移除此项
	})
	
	$(document).on("click",".m-select-r li", function () {
		$('.m-select').removeClass('on');
		$(this).find('.arrow-d-2').removeClass('on');
		$('.mask-layer-2').remove();
		$('body').css({'overflow-y':'auto'});//恢复body纵向滚动条
		$('.'+$(this).parent().parent().attr('id')+' span').text($(this).text());//取值
		$(this).addClass('current').siblings().removeClass('current');
	});
	$(document).on("click",".mask-layer-2", function () {
		$('.m-select').removeClass('on');
		$('.m-select-wrapper,.linkage-select,.m-select-wrapper2').find('.arrow-d-2').removeClass('on');
		$('.mask-layer-2').remove();
		$('body').css({'overflow-y':'auto'});//恢复body纵向滚动条
	});
	//点击li时添加current样式
	$('.m-select li').not('.hold li').click(function(){
		$(this).addClass('current').siblings().removeClass('current');
	});
	//省市联动选择 初始化
	if($(this).find('.form-g-text').text()==$(this).find('.form-g-text').data('default'))
		{
			$('#'+$(this).find('.form-g-each-r').data('role')).removeClass('with-sub');
		} else $('#'+$(this).find('.form-g-each-r').data('role')).addClass('with-sub');
	//根据用户历史选择项（数据库中已存储选项）,为当前选择项添加样式
	$('.m-select-r li,.m-select li').each(function(){
		if($(this).text()==$(this).parents('.m-select').prev('.m-select-wrapper').find('.form-g-text').text())
		{
			$(this).addClass('current').siblings().removeClass('current');
		}
	})
	//控制二级select面板是否显示
	$('.m-select-with-sub').click(function(){
		if($(this).find('.form-g-text').text()==$(this).find('.form-g-text').data('default'))
		{
			$('#'+$(this).find('.form-g-each-r').data('role')).removeClass('with-sub');
		} else $('#'+$(this).find('.form-g-each-r').data('role')).addClass('with-sub');
	});
	//点击select左侧面板选项时，展开右侧二级面板
	$('.m-select-l li').click(function(){
		$(this).parents('.m-select').addClass('with-sub');
		$('.m-select-r').show();
	});
	
	/*********linkage-select*********/
	$('.linkage-select .form-g-each-r,.linkage-select-trigger').click(function(){
		$(this).find('.arrow-d-2').addClass('on');
		$('body').append('<div class="mask-layer-2"></div>');
		$('.mask-layer-2').show();
		$('#'+$(this).data('role')).addClass('on');
		$(this).addClass($(this).data('role'));
		$('#'+$(this).data('role')).find('.first-step').show().find('.linkage-selected').html('选择省份');
		$('#'+$(this).data('role')).find('.second-step').hide();
	});
	$(document).on("click",".mask-layer-2", function () {//点击空白区域，关闭弹出层
		$('.linkage-select .form-g-each-r').find('.arrow-d-2').removeClass('on');
		$('.linkage-select-panel').removeClass('on');
		$('.mask-layer-2').remove();
	});
	var linkage_selected='';//定义变量，存储第一步已选择的数据信息（如省）
	$('.linkage-select-panel .first-step li').click(function(){
		linkage_selected=$(this).text();
		$(this).parents('.first-step').find('.linkage-selected').text(linkage_selected);
		$(this).parents('.first-step').hide();//关闭第一步
		$(this).parents('.linkage-select-panel').find('.second-step').show().find('.linkage-selected').html('<span class="first">'+linkage_selected+'</span>'+'>'+'选择城市');//打开第二步 传值
	});
	//
	var linkage_selected2='';//定义变量，存储第二步已选择的数据信息（如市）
	$('.linkage-select-panel .second-step li').click(function(){
		linkage_selected2=$(this).text();
		$(this).parents('.linkage-select-panel').find('.linkage-selected').html('<span class="first">'+linkage_selected+'</span>'+'>'+'<span class="orange">'+linkage_selected2+'</span>');
		$(this).parents('.second-step').hide();
		$(this).parents('.linkage-select-panel').removeClass('on');
		$('.mask-layer-2').remove();
		$('.'+$(this).parents('.linkage-select-panel').attr('id')+' span').text(linkage_selected+' '+linkage_selected2);//取值
		$('.'+$(this).parents('.linkage-select-panel').attr('id')+' .out-input').text(linkage_selected+' '+linkage_selected2);//取值
	});
	//允许回选
	$('.linkage-select-panel .second-step .linkage-selected').on('click','.first',function(){
		$(this).parents('.second-step').hide();
		$(this).parents('.linkage-select-panel').find('.first-step').show().find('.linkage-selected').html(linkage_selected+'</span>'+'>'+'选择城市');;
	})
	
	/**********linkage-select end*********/
	//tab
	$('.tab-g-t li').click(function(){
		var liindex = $('.tab-g-t li').index(this);
		$(this).addClass('current').siblings().removeClass('current');
		$('.tab-g-each').eq(liindex).show().siblings('.tab-g-each').hide();
	});
	//文本框获得焦点时
	$('.form-g-input').focus(function(){$(this).parents('.form-g-each').addClass('input-focus')});
	//文本框失去焦点时
	$('.form-g-input').blur(function(){$(this).parents('.form-g-each').removeClass('input-focus')});
	//radio
	$('.radio-input').each(function(){
		if($(this).attr('checked')=='checked'){$(this).parents('.form-g-radio-each').addClass('on');}
	});
	$('.form-g-radio-each').click(function(){$(this).addClass('on').attr('checked','checked').siblings().removeClass('on').attr('checked','');})
	//checkbox
	$('.form-g-checkbox').click(function(){
		$(this).find('.c').toggleClass('active');
	});
	//补充底部模板footer的高度
	function footer_height_supply(){$('.footer-wrapper').height($('.footer-wrapper .footer').height());}
	footer_height_supply();
	$(window).resize(function(){
		footer_height_supply();
	});
})
//////////////////////////////Message 对象///////////////////////////////////////////
//创建Loading对象
//创建Message对象
function Message(){
}
var msgFlag=true;//用于标志关闭函数是否已执行/回调函数是否已调用
//定义信息关闭函数
function msgClose(){
	$('body').find('.tui-message').remove();
	msgFlag=false;
}
//show
Message.prototype.show=function(data){//msg type time shade shadeClose position confirm
	msgFlag=true;
	//msg
	data.msg?this.msg=data.msg:this.msg='加载中...';
	$('body').append('<div class="tui-message"></div>');
	$(".tui-message").css("z-index","10005");
	$('.tui-message').height($(window).height());//message的高度等于窗口的高度
	//shade
	switch(data.shade){
		case false://false情况下不显示遮罩层
		break;
		default://其余情况下显示遮罩层 参数可为空
		$('.tui-message').append('<div class="tui-mask"></div>');
		break;
	}
	//shadeClose
	switch(data.shadeClose){
		case false://false情况下点击遮罩层不关闭信息
		break;
		default://其余情况下点击遮罩层关闭信息 参数可为空
		$('.tui-mask')?$('.tui-mask').click(function(){if(msgFlag){msgClose();data.fn?data.fn():'';}}):'';
		break;
	}
	
	//type
	switch(data.type){
		case 1://提示信息
		$('.tui-message').append('<div class="tui-tip"><div class="tui-tip-bg"></div><div class="tui-tip-text"><p>'+data.msg+'</p></div></div>');
		$('.tui-message').find('.tui-mask').addClass('tui-mask-tip');//为提示信息遮罩层添加样式tui-mask-tip
		//confirm
		if(data.confirm){
			$('.tui-message').find('.tui-mask').removeClass('tui-mask-tip');
			$('.tui-tip-text').append('<div class="tui-tip-confirm"><input type="button" value="是" class="yes"/><input type="button" value="否" class="no"/></div>');
			data.confirm.yes?$('.tui-tip-confirm .yes').val(data.confirm.yes):'';//自定义确定按钮文字
			data.confirm.yes?$('.tui-tip-confirm .no').val(data.confirm.no):'';//自定义取消按钮文字
			//yes
			$('.tui-tip-confirm').on('click','.yes',function(){
				if(msgFlag){msgClose();data.fn?data.fn():'';};
				if(data.confirm.fn){data.confirm.fn()}//点击确定按钮后，如果有回调函数，则执行
			})
			//no
			$('.tui-tip-confirm').on('click','.no',function(){
				if(msgFlag){msgClose();data.fn?data.fn():'';};
				if(data.confirm.fn2){data.confirm.fn2()}//点击取消按钮后，如果有回调函数，则执行
			})
		}
		$('.tui-message').find('.tui-tip-bg').height($('.tui-tip-text').height());
		break;
		case 2:
		alert(2);
		break;
		default://不传值的话(undefined),默认为loading
		//loading
		$('.tui-message').append('<div class="tui-loading"><div class="tui-loading-bg"></div><span class="tui-loading-icon"></span><div class="tui-loading-text">'+this.msg+'</div></div>');
		break;
	}
	
	//position
	switch(data.position){
		case 'top'://top
		$('.tui-tip').length?$('.tui-tip').css({'top':0}):'';
		break;
		case 'bottom'://bottom
		$('.tui-tip').length?$('.tui-tip').css({'top':'100%','margin-top':-$('.tui-tip-text').height()-30}):'';
		break;
		default://默认 middle
		$('.tui-tip').length?$('.tui-tip').css({'top':'50%','margin-top':-$('.tui-tip-text').height()/2-15}):'';
		break;
	}

	//time
	if(data.type==1 && !data.confirm){//type为1，同时非confirm模式下
		setTimeout(function(){if(msgFlag){msgClose();data.fn?data.fn():'';};},2000);
	}
	else{//其余情况
		data.time?setTimeout(function(){if(msgFlag){msgClose();data.fn?data.fn():'';};},data.time):'';
	}
	return this;
}
//close
Message.prototype.close=function(){
	msgClose();
	return this;
}
//////////////////////////////Message 对象 end///////////////////////////////////////////
//判断页面上的值有没有改动
function IsFormChanged() {
    var isChanged = false;
    var form = document.forms[0];
    for (var i = 0; i < form.elements.length; i++) {
        var element = form.elements[i];
        var type = element.type;
        if (type == "text" || type == "radio" || type == "span") {
            if (element.value != element.defaultValue) {
                isChanged = true;
                break;
            }
        }
    }
    return isChanged;
}

//计算天数差的函数，通用  
function getDateDiff(startDate,endDate){  
	if(	startDate == null||startDate==''){
		return "7天前";
	}
    var startTime = new Date(startDate).getTime()    
    var endTime = new Date(endDate).getTime();   
    var dates = Math.round(Math.abs((endTime - startTime))/(1000*60*60*24));     
    if(dates == 0){
		return "今天";
	}
    if(dates<7){
    	return dates + "天前";
    }else{
    	return "7天前";
    }
}   