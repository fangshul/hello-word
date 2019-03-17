# hello-word
document.oncontextmenu = function(){
　　return false;
}
$(document).ready(function(){
	var oldhtml='';
	
	// 个人信息部分
	var perTop = $("#body-box").offset().top;
	var perLeft = $("#body-box").offset().left;
	$(".personal-information").append($("<img>")).hide();
	$(".openportrait").hide();
	$(".personal-information").children("img").attr("src",$(".portrait")[0].src)
	.css({"height":"75px","width":"75px","border-radius":"3px","position":"absolute","right":"40px","top":"35px","cursor":"pointer"})
	.click(function(){
		$(".openportrait").show();
		$(".personal-information").hide();
	});
	$(".openportrait").append($("<img>"));
	$(".openportrait").children("img").attr("src",$(".portrait")[0].src).css({"width":"413px","height":"347px"})
	$("#close-openportrait").click(function(){
		$(".openportrait").hide();
	});
	$('.portrait').click(function(e){
		$(".personal-information").toggle();
		var mouseLeft = e.originalEvent.x||e.originalEvent.laterX||0;
		var mouseTop = e.originalEvent.y||e.originalEvent.layerY||0;
		$('.personal-information').css({"position":"absolute","top":mouseTop-perTop+"px","left":mouseLeft-perLeft+"px"});
		console.log(mouseTop-perTop);
	});
	// 侧边导航栏
	// 聊天
	$("#chat").click(function(){
		$("#chat span").html("&#xe61b;").attr("class","LargeRange-iconfont-message-2");
		$(".chat-bottom").show();
		$("#chatContentXiaolan").show();
		$("#other").hide();
		
		if($("#address-book").prop("className")=="address-book-"){
			$("#address-book").attr({"src":"images/address-book.png","class":"address-book"});
			$("#address-book").hover(function(){$("#address-book").attr("src","images/hover-address-book.png")},
			function(){$("#address-book").attr("src","images/address-book.png")});	
		}
	
		if($("#collect span").prop("className")=="iconfont-collect-2"){
			$("#collect span").html("&#xe64c;").attr("class","iconfont-collect");
		}
		
		$(".talk").show();
		$(".address-book-box").hide();
		$(".collect-box").hide();
		$(".search-close").trigger("click");
	});
	// 通信录
	$("#address-book").hover(function(){$("#address-book").attr("src","images/hover-address-book.png")},
			function(){$("#address-book").attr("src","images/address-book.png")});	
	$("#address-book").click(function(){
		$("#address-book").attr({"src":"images/click-address-book.png","class":"address-book-"})
		$(".chat-bottom").hide();
		$("#chatContentXiaolan").hide();
		$("#other").show().css({"background-image":"url(images/background.png)","background-size":"cover"});
		$("#address-book").hover(function(){$("#address-book").attr("src","images/click-address-book.png")},
			function(){$("#address-book").attr("src","images/click-address-book.png")});		
		
		
		if($("#chat span").prop("className")=="LargeRange-iconfont-message-2"){
			$("#chat span").attr({"class":"LargeRange-iconfont-message"}).html("&#xe600;");
		}
		if($("#collect span").prop("className")=="iconfont-collect-2"){
			$("#collect span").html("&#xe64c;").attr("class","iconfont-collect");
		}
		
		$(".talk").hide();
		$(".address-book-box").show();
		$("#chatting-name").html("");
		$(".collect-box").hide();
		$(".search-close").trigger("click");
	});
	// 收藏
	$("#collect").click(function(){
		$("#collect span").html("&#xe729;").attr("class","iconfont-collect-2");
		$(".chat-bottom").hide();
		$("#other").show().css({"background-image":"url(images/background.png)","background-size":"cover"});
		$("#chatting-name").html("全部收藏");
		$(".collect-box").show();
		$(".talk").hide();
		$(".address-book-box").hide();
		$("#chatContentXiaolan").hide();

		if($("#address-book").prop("className")=="address-book-"){
			$("#address-book").attr({"src":"images/address-book.png","class":"address-book"});
			$("#address-book").hover(function(){$("#address-book").attr("src","images/hover-address-book.png")},
			function(){$("#address-book").attr("src","images/address-book.png")});	
		}
		if($("#chat span").prop("className")=="LargeRange-iconfont-message-2"){
			$("#chat span").attr({"class":"LargeRange-iconfont-message"}).html("&#xe600;");
		}
		$(".search-close").trigger("click");
	});
	// 选择聊天框
		//关闭 
		$("#search input").click(function(){
			$("#search-close").show();
			$("#search").css({"background-color":"rgb(248,248,248)"});
			$("#search input").css({"background-color":"rgb(248,248,248)"}).attr({"placeholder":""});
			$(".talk").hide();
			$(".address-book-box").hide();
			$(".search-content").show();
			$(".collect-box").hide();
		});
		$("#search-close").click(function(){
			$("#search-close").hide();
			$("#search").css({"background-color":"rgb(219,217,216)"});
			$("#search input").css({"background-color":"rgb(219,217,216)"}).attr({"placeholder":"搜索","value":""});
			$(".search-content").hide();
			if($("#chat span").prop("className")=="LargeRange-iconfont-message-2"){
				$(".talk").show();
				$(".address-book-box").hide();
				$(".collect-box").hide();
			}
			if($("#address-book").prop("className")=="address-book-"){
				$(".address-book-box").show();
				$(".talk").hide();
				$(".collect-box").hide();
			}
			if($("#collect span").prop("className")=="iconfont-collect-2"){
				$(".address-book-box").hide();
				$(".talk").hide();
				$(".collect-box").show();
			}
		});
		// 聊天框
		$("#pushpin").hover(function(){$("#pushpin").attr("src","images/pushpin-hover.png")},
			function(){
				$("#pushpin").attr("src","images/pushpin.png");
			});
		$("#talk-1").click(function(){
			choice("#talk-1");
		});	
		$("#talk-2").click(function(){
			choice("#talk-2");
		});	
		$("#talk-3").click(function(){
			choice("#talk-3");
		});	
		$("#talk-4").click(function(){
			choice("#talk-4");
		});
		//发送消息
		var ti=new Array();
		var tis=0;
		$(".send").click(function(){
			
			
			if($("#chatting-name").html()==$('#talk-1-name').html()){
				reply("#chatContentXiaolan");
			}
			if($("#chatting-name").html()==$('#talk-2-name').html()){
					reply("#chatContentWy");
				}
			if($("#chatting-name").html()==$('#talk-3-name').html()){
				reply("#chatContentFile");
			}
			if($("#chatting-name").html()==$('#talk-4-name').html()){
				reply("#chatContentVipcn");
			}
			var times = new Date();
			ti[tis]=times.getMinutes();
			tis++;

		});
		setInterval(function(){
			if(ti[tis-1]-ti[tis-2]<1){
				$(".replybox").eq(tis-1).children().eq(0).hide();
				}
		},50);
		// 点击搜聊天记录
		$(".search-record-input").click(function(){
			$(".search-record-input input").css("background-color","rgb(250,250,250)").attr("placeholder","");
		});
		$(".records-box-head").click(function(){
			$(".search-record-input input").css("background-color","rgb(232,232,232)").attr("placeholder","搜聊天记录");
		});
		$(".record-box-body").click(function () {
			$(".search-record-input input").css("background-color","rgb(232,232,232)").attr("placeholder","搜聊天记录");
		});
		$(".records").click(function () {
			$(".records-box").show();
			$(".talk").show();
			$(".search-content").hide();
			$("#search-close").hide();
			$("#search").css({"background-color":"rgb(219,217,216)"});
			$("#search input").css({"background-color":"rgb(219,217,216)"}).val("").attr("placeholder","搜索");
		});
		$("#close-record").click(function () {
			// body...
			$(".records-box").hide();
		});
		// 点击搜一搜
		$(".try-to-search-box").click(function(){
			$(".try-to-search-box input").css("background-color","rgb(250,250,250)").attr("placeholder","");
		});
		$(".try-box").click(function () {
			$(".try-to-search-box input").css("background-color","rgb(232,232,232)").attr("placeholder","搜聊天记录");
		});
		$(".article-search").click(function () {
			$(".try-to-search-box").show();
			$(".search-content").hide();
			$("#search-close").hide();
			$("#search").css({"background-color":"rgb(219,217,216)"});
			$("#search input").css({"background-color":"rgb(219,217,216)"}).val("").attr("placeholder","搜索");
			$(".talk").show();
		});
		$("#close-try").click(function () {
			$(".try-to-search-box").hide();
		});
		//聊天人的信息
		$(".iconfont-switch-off").click(function () {
			$(".iconfont-switch-on").css("display","inline-block");
			$(".iconfont-switch-off").css("display","none");
			if($("#chatting-name").html()==$("#talk-1-name").html()&&$(".iconfont-switch-on").css("display")=="block"){
				$(".message-free-xiaolan").hide();
			}
			 if($("#chatting-name").html()==$("#talk-2-name").html()&&$(".iconfont-switch-on").css("display")=="block"){
				$(".message-free-wy").hide();
			}
			 if($("#chatting-name").html()==$("#talk-3-name").html()&&$(".iconfont-switch-on").css("display")=="block"){
				$(".message-free-file").hide();
			}
			if($("#chatting-name").html()==$("#talk-4-name").html()&&$(".iconfont-switch-on").css("display")=="block"){
				$(".message-free-vipcn").hide();
			}
		});
		$(".iconfont-switch-on").click(function(){
			$(".iconfont-switch-on").css("display","none");
			$(".iconfont-switch-off").css("display","inline-block");
			console.log($(".iconfont-switch-off").css("display"));
			if($("#chatting-name").html()==$("#talk-1-name").html()&&$(".iconfont-switch-off").css("display")=="block"){
				$(".message-free-xiaolan").show();
				
			}
			 if($("#chatting-name").html()==$("#talk-2-name").html()&&$(".iconfont-switch-off").css("display")=="block"){
				$(".message-free-wy").show();
			}
			 if($("#chatting-name").html()==$("#talk-3-name").html()&&$(".iconfont-switch-off").css("display")=="block"){
				$(".message-free-file").show();
			}
			if($("#chatting-name").html()==$("#talk-4-name").html()&&$(".iconfont-switch-off").css("display")=="block"){
				$(".message-free-vipcn").show();
			}
		});
		$(".iconfont-stick-off").click(function () {
			$(".iconfont-stick-off").css("display","none");
			$(".iconfont-stick-on").css("display","inline-block");
		});
		$(".iconfont-stick-on").click(function () {
			$(".iconfont-stick-off").css("display","inline-block");
			$(".iconfont-stick-on").css("display","none");
		});
		var l=0;
		$(".more").click(function(){
			l++;
			$(".daverse-information").toggle();
			if(l%2!=0){
				$("#body-box").css("width","1330px");
			}
			else{
				$("#body-box").css("width","1060px");
			}

		});
	
		$(".chatting").children().not(".more").click(function(){
			if($(".daverse-information").css("display")=="block"){
				l++;
				$(".daverse-information").hide();
				$("#body-box").css("width","1060px");}
		});
		$("#body-box").children().not(".chatting").not(".daverse-information").click(function(){
			if($(".daverse-information").css("display")=="block"){
				l++;
				$(".daverse-information").hide();
				$("#body-box").css("width","1060px");}
		});
		// 收藏各部分
		$(".collect-box").children().not($(".new-collect-box")).click(function(){
			if($(this).attr("class").indexOf("-")<0){
				$(this).attr("class",$(this).attr("class")+"-");
				if($(this).attr("class").indexOf("album")>=0){
						$(".x").css("background-color","rgb(202,200,198)");
					}
			}
			var len = $(".collect-box").children().not($(".new-collect-box")).not($(this)).length;
			var othercol = $(".collect-box").children().not($(".new-collect-box")).not($(this));
			for(var i=0;i<len;i++){
				if(othercol.eq(i).attr("class").indexOf("-")>=0){
					othercol.eq(i).attr("class",othercol.eq(i).attr("class").substring(0,othercol.eq(i).attr("class").length-1));
					if(othercol.eq(i).attr("class").indexOf("album")>=0){
						$(".x").css("background-color","rgb(238,234,232)");
					}
					break;
				}
			}
		});
		// 撤回
		var recall = document.getElementsByClassName('recall');
		var replybox = document.getElementsByClassName('replybox');
		setInterval(function(){
		for(var a=0;a<recall.length;a++){
			
			recall[a].onclick=function(){
				recalls(this);

			}
			
		}
		},1000);
		// 删除
		var deletes = document.getElementsByClassName('deletes');
		setInterval(function(){
			for(var b=0;b<deletes.length;b++){
				
				deletes[b].onclick=function () {
					deletex(this);
				}
			}
		},1000);

		$(".remark input").keydown(function(e){
			if(!e)e=window.event;
			if((e.keyCode || e.which) == 13){
				$(".chatting-name").html($(".remark input").val());
				if($("#chatContentXiaolan").css("display")=="block"){
					$("#talk-1-name").html($(".remark input").val());
				}
				if($("#chatContentWy").css("display")=="block"){
					$("#talk-2-name").html($(".remark input").val());
				}
				if($("#chatContentFile").css("display")=="block"){
					$("#talk-3-name").html($(".remark input").val());
				}
				if($("#chatContentVipcn").css("display")=="block"){
					$("#talk-4-name").html($(".remark input").val());
				}
			}
		});
	$(".daverse-information img").click(function(){
		$(".detailed-information").toggle();
	});
	$(".open-o-portrait").hide();
	$(".imgs").click(function(){
		$(".open-o-portrait").show();
	});
	$("#close-open-o-portrait").click(function(){
		$(".open-o-portrait").hide();
	});
	$("#word").keydown(function(event){
		if(event.keyCode==13){
			$(".send").click();
		}
	});

});
function choice(obj){
	var x,l;
	if(obj=="#talk-1"){x=1;l="Xiaolan";}
	else if(obj=="#talk-2"){x=2;l="Wy";}
	else if(obj=="#talk-3"){x=3;l="File";}
	else if(obj=="#talk-4"){x=4;l="Vipcn";}
	
	$("#chatting-name").html($("#talk-"+x+"-name").html());
	$(".chat-content").not($("#chatContent"+l)).hide();
	$("#chatContent"+l).show();
	$(".daverse-information img","imgs",".open-o-portrait img").attr("src",$("#talk-portrait-"+x).attr("src"));
	$("#talk-"+x).css("background-color","rgb(198,197,197)");
	$(".talk").children().not($("#talk-"+x)).css({"background-color":"rgb(238,234,232)"})
	
	$(".s-name").html($("#chatting-name").html());
	$(".remark input").attr({"value":"$('#chatting-name').html()"});
	oldhtml=$("#talk-"+x+"-name").html();
	
}
var x=0;
var w=0;
var f=0;
var v=0;
var  r=1;
var z=0;
function reply(id){

	if($(id).attr("id")=="chatContentXiaolan"){x++;}
	else if($(id).attr("id")=="chatContentWy"){w++;}
	else if($(id).attr("id")=="chatContentFile"){f++;}
	else if($(id).attr("id")=="chatContentVipcn"){v++;}

	// 发送的内容
	var div = $("<div class='replybox'></div>");
	var html=
		'<div class="time">'+time()+'</div>'+
		'<div class="comment-left">'+'<img class="mineImg">'+'</div>'
		+'<div class="comment-right" onmousedown="whichButton(event,this)">'
		+'<div class="cornule">'+'</div>'
		+'<div class="comment-text">'+$(".word").val()+'</div>'+'</div>'
		+'<div class="mine-right-hand">'
		+'<div class="copy">'+"复制"+'</div>'
		+'<div class="recall">'+"撤回"+'</div>'
		+'<div class="transmit">'+"转发"+'</div>'
		+'<div class="favorite">'+"收藏"+'</div>'
		+'<div class="multiselect">'+"多选"+'</div>'
		+'<div class="cite">'+"引用"+'</div>'
		+'<div class="translate">'+"翻译"+'</div>'
		+'<div class="deletes">'+"删除"+'</div>';
	div.html(html);
	var chi = $(id).children()[0];
	
	
	if(x>r){
		
		z=z+2;
	}

	if(x>1){
		r++;
	}
	if($(id).attr("id")=="chatContentXiaolan"&&x>1){ 
		
		
		div.css("top",parseInt($(id).children().eq(z-1).css("top"))+30+"px");
		

	}
	if($(id).attr("id")=="chatContentWy"&&w>1){

		div.css("top",parseInt($(id).children().eq(z-1).css("top"))+30+"px");
	}
	if($(id).attr("id")=="chatContentFile"&&f>1){
		div.css("top",parseInt($(id).children().eq(z-1).css("top"))+30+"px");
	}
	if($(id).attr("id")=="chatContentVipcn"&&v>1){
		div.css("top",parseInt($(id).children().eq(z-1).css("top"))+30+"px");
	}
	$(id).append(div);
	$("#word").val("");
	$(".mineImg").attr("src",$("#portrait").attr("src"));

	var divtwo = $("<div class='replybox-2'></div>");
	var htmltwo =
	'<div class="daverse-left">'+'<img class="daverseImg">'+'</div>'
	+'<div class="daverse-right">'+'<div class="cornule-2">'+'</div>'+"收到"+'</div>'
	divtwo.html(htmltwo);
	if($(id).attr("id")=="chatContentXiaolan"&&x==1){ 
		divtwo.css("top",div.children().eq(2).height()+60+"px");
		
	}
	if($(id).attr("id")=="chatContentWy"&&w==1){
		divtwo.css("top",div.children().eq(2).height()+60+"px");
	}
	if($(id).attr("id")=="chatContentFile"&&f==1){
		divtwo.css("top",div.children().eq(2).height()+60+"px");
	}
	if($(id).id=="chatContentVipcn"&&v==1){
		divtwo.css("top",div.children().eq(2).height()+60+"px");
	}
	if($(id).attr("id")=="chatContentXiaolan"&&x>1){
		divtwo.css("top",div.children().eq(2).height()+parseInt(div.css("top"))+60+"px");
	}
	if($(id).attr("id")=="chatContentWy"&&w>1){
		divtwo.css("top",div.children().eq(2).height()+parseInt(div.css("top")).top+60+"px");
	}
	if($(id).attr("id")=="chatContentFile"&&f>1){
		divtwo.css("top",div.children().eq(2).height()+parseInt(div.css("top"))+60+"px");
	}
	if($(id).attr("id")=="chatContentVipcn"&&v>1){
		divtwo.css("top",div.children().eq(2).height()+parseInt(div.css("top"))+60+"px");
	}
	$(id).append(divtwo);

	if($("#chatting-name").html()==$("#talk-1-name").html()){
		$(".daverseImg").attr("src",$("#talk-portrait-1").attr("src"));
		
	}
	 if($("#chatting-name").html()==$("#talk-2-name").html()){
		$(".daverseImg").attr("src",$("#talk-portrait-2").attr("src"));
	}
	 if($("#chatting-name").html()==$("#talk-3-name").html()){
		$(".daverseImg").attr("src",$("#talk-portrait-3").attr("src"));
	}
	if($("#chatting-name").html()==$("#talk-4-name").html()){
		$(".daverseImg").attr("src",$("#talk-portrait-4").attr("src"));
		
	}
	// 获取时间
	function time(){
		var t = new Date();
		var h = t.getHours();
		var m = t.getMinutes();
		h=h<10?"0"+h:h;
		m=m<10?"0"+m:m;

		return h+":"+m;
	}
	$(id).scrollTop($(id)[0].scrollHeight);
	
}

function recalls(obj){
	var comright = $(obj).parent().prev();
	comright.hide().prev().hide();
	var hint = $("<div class='hint'></div>");
	hint.html("你撤回了一条消息");
	$(obj).parent().prev().parent().append(hint);
	var replytwo = $(obj).parent().prev().parent().next();
	console.log(parseInt(replytwo.css("top")));
	console.log(parseInt(comright.css("height")));
	replytwo.css("top",parseInt(replytwo.css("top"))-parseInt(comright.css("height"))+30+"px");
	var reedit = $("<a href='javascript:;'>重新编辑</a>");
	hint.append(reedit);
	var content = comright.children().eq(1).html();
	reedit.click(function(){
		$("#word").val(content);
	}).hover(function(){reedit.css("text-decoration","underline");},function(){reedit.css("text-decoration","none");});
	allreply = $(obj).parent().parent().parent().children();
	for(var f=0;f<(allreply.length);f++){
		
		if(allreply.eq(f).index()==($(obj).parent().parent().index())){
			
			for(var d=f+2;d<allreply.length;d++){
				
				if(allreply.eq(d).attr("class")=="replybox"){
					allreply.eq(d).css("top",parseInt(allreply.eq(d-1).css("top"))+30+"px");
					console.log("r");
					console.log(allreply.eq(d).css("top"));
				}
				else if(allreply.eq(d).attr("class")=="replybox-2"){
					allreply.eq(d).css("top",parseInt(allreply.eq(d-1).css("top"))+parseInt(allreply.eq(d-1).children().eq(2).css("height"))+60+"px");					
					console.log("r-2");
				}
			}
		break;	
		}
		
	}
}
function deletex(obj){
	var comRight=$(obj).parent().prev();
	comRight.hide().prev().hide();
	var replybox = $(obj).parent().parent();
	 replybox.css("height","40px");
	 replybox.next().css("top",parseInt($(obj).parent().parent().next().css("top"))-parseInt(comRight.css("height"))+20+"px")
	for(var t=0;t< replybox.parent().children().length;t++){
		if(replybox.parent().children().eq(t).index()==$(obj).parent().parent().index()){
			for(var h=t+2;h< replybox.parent().children().length;h++){
				if(replybox.parent().children().eq(h).attr("class")=="replybox"){
					replybox.parent().children().eq(h).css("top",parseInt(replybox.parent().children().eq(h-1).css("top"))+20+"px");			
				}
				else if(replybox.parent().children().eq(h).attr("class")=="replybox-2"){
					replybox.parent().children().eq(h).css("top",parseInt(replybox.parent().children().eq(h-1).css("top"))+parseInt(replybox.parent().children().eq(h-1).children().eq(2).css("height"))+50+"px");			
				}
			}	
		}
		break;
	}
}
function whichButton(event,obj){
	var comright=$(obj).parent();
	if(event.button==2){
		comright.find(".mine-right-hand").show();
	}
}
function whichButtons(event){
	if(event.button==0){
		for(var i=0;i<$(".mine-right-hand").length;i++){
			$(".mine-right-hand").eq(i).hide();
		}
	}
}
function onlyread(){
	var oldhtml=$("#talk-1-name").html();
	$(".remark input").attr("readonly",true).css("border","none");
	if($("#chatContentXiaolan").css("display")=="block"){
		$("#talk-1-name").html($(".remark input").val());
	}
	if($("#chatContentWy").css("display")=="block"){
		$("#talk-2-name").html($(".remark input").val());
	}
	if($("#chatContentFile").css("display")=="block"){
		$("#talk-3-name").html($(".remark input").val());
	}
	if($("#chatContentVipcn").css("display")=="block"){
		$("#talk-4-name").html($(".remark input").val());
	}
	$("#chatting-name").html($(".remark input").val());
}
function change() {
	$(".remark input").attr("readonly",false).css("border","1px solid #9B9A9A");
}
