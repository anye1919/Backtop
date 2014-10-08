Backtop
=======


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

