
# Tabs Click 
```javascript
$('.section_tab').each(function() {
    $(this).find('.section').hide();

    var current = $(this).find('.item_title_tab').children('.current');
    if (current.length == 0) {
      $(this).find('.item_title_tab').children(':first-child').addClass('current');
      $($(this).find('.item_title_tab').children(':first-child').find('a').attr('href')).show();
    }

    $(this).find('.item_title_tab').find('a').click(function() {
      var current = $(this).parent().hasClass('current');
      if (current == false) {
        $(this).parent()
          .addClass('current')
          .siblings().each(function() {
            $(this).removeClass('current');
            $($(this).find('a').attr('href')).hide();
          });
        $($(this).attr('href')).fadeIn();
      }
      return false;
    });
  });
  ```
  # Tabs Click FUNCTION
  ```javascript
  $.NAME.tabLayout = function(options){
		var defaults = {
			parent_tab: $('.tab .tab-pane'),
			tab_click: '.tab_ttl',
			tab_cnt: $('#tmp_infor_tab .tab_infor_cnt'),
			winW: 480,
		},
		s = $.extend(defaults, options);
		/*---- INIT ----*/
		click_tab();
		/*---- PRIVATE FUNCTION ----*/
		function click_tab() {
			$(s.parent_tab).each(function(){
				$(this).find($(s.tab_click)).click(function(){
					var iscurrent = $(this).parent().hasClass('active');
					if(!s.sp || $(window).width() > s.winW || $('body').hasClass('disp_pc')) {
						if(!iscurrent){
							$(s.parent_tab).removeClass('active');
							$(s.tab_cnt).hide();
							$(this).parent().addClass('active');
							$(this).next().show();
						}
					}else{
						var iscurrent = $(this).parent().hasClass('active');
						if(iscurrent){
							$(this).parent().removeClass('active');
							$(this).next().slideUp(300);
						}else {
							$(this).parent().addClass('active');
							$(this).next().slideDown(300);
						}
					}
					return false;
				});
				
			});
		}
		function reset_active() {
			$(s.tab_click).parent().removeClass('active');
			$(s.tab_cnt).css('display','');
			if(!s.sp || $(window).width() > s.winW || $('body').hasClass('disp_pc')){
				$(s.parent_tab).each(function(index){
					if(!$(this).hasClass('active') && index == 0) $(this).addClass('active');
				});
			}
		}
		/*---- PUBLIC ----*/
		return {
			resize: function() {
				reset_active();	
			}
		}
	};
  ```
 ### Sử dụng
  ```javascript
  //============================================================================
	//============================================================================
	var tabSwitch = new $.GFUNC.tabLayout({
	parent_tab: $('#tmp_infor_tab .infor_tab'),
	tab_click: '.tab_infor_ttl',
	tab_cnt: $('#tmp_infor_tab .tab_infor_cnt'),
  ```