# FloatingNaviLef
```javascript
	var setFloatingNavi = function(options){
		var naviObj = $('#header');
		var wrapObj = $('#wrapper');
		var mainObj = $('#main_content');
	    $(window).on("scroll resize", function() {
			var h = naviObj.height();
			var naviOriginalHeight = h;
			var h2 = $(window).height();
			var mh = mainObj.height();
			var decH = h - h2;
			var scrLeft = $(this).scrollLeft() * -1;
			if(h > mh) {
				return false;
			}
			if ($(this).scrollTop() > decH && $(window).width() > 640) {
				if(naviObj.hasClass('fix_pos')){
					naviObj.removeClass('fix_pos');
				}
				naviOriginalHeight = naviObj.height();
				naviObj.addClass('fix_pos');
				var mg = wrapObj.css('marginLeft');
				var set = mg;
				if(scrLeft != 0) set = scrLeft;
				naviObj.css({
				left:set
				});
			} else {
				naviObj.removeClass('fix_pos');
				naviObj.css({
					left:'auto'
				});
			}
			// 大画面用 windowサイズがgnavi領域より高さを持つ場合はtop:0;にする
			if(naviOriginalHeight <= h2) {
				naviObj.css({
					top:0
				});
			} else {
				naviObj.css({
					top:'auto'
				});
			}
		});
    }
    if($('#header').length){
        setFloatingNavi();// 追従メニュー
    }
  ```
