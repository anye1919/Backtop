Backtop
=======

*JS实现回到顶部效果*

```JavaScript
window.onload = function() {
	var backtop = document.getElementById("backtop");
	var timer = null;
	var isTop = true;
	var clientHeight = document.documentElement.clientHeight;

	window.onscroll = function(){
		var osTop = document.documentElement.scrollTop || document.body.scrollTop;
		if(osTop >= clientHeight) {
			backtop.style.display = "block";
		} else {
			backtop.style.display = "none";
		}
		if(!isTop) {
			clearInterval(timer);
		}
		isTop = false;
	};

	backtop.onclick = function() {
		timer = setInterval(function(){
			var osTop = document.documentElement.scrollTop || document.body.scrollTop;
			var ispeed = Math.floor(-osTop / 6);
			document.documentElement.scrollTop = document.body.scrollTop = osTop + ispeed;

			isTop = true;
			if(osTop == 0) 
				clearInterval(timer);
		}, 30);
	};
};

 var initAppView = function() {
     var fromType = getParameter("fromType");
     if (fromType.indexOf("app") > -1 && window.location.href.indexOf('/page/game_') > -1) {
         var timer = setInterval(function() {
             var header = document.getElementsByTagName('header')[0];
             var footer = document.getElementsByTagName('footer')[0];
             if (header) {
                 header.style.display = 'none';
             }
             if (footer) {
                 footer.style.display = 'none';
                 clearInterval(timer);
             }
         }, 1)
     }
   };
```
