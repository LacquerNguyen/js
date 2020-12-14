# MenuSp
```javascript
var settingMenuSp = {
    init: function() {
        settingMenuSp.bind();
    },
    bind: function() {
        var $menuBtn = $('.mobile_control li a');
        var $closeBtn = $('.close_btn a');
        $menuBtn.on('click', function(e) {
            var _this = $(this);
            var _id = _this.attr('href');
            if ($(_id).length > 0) {
                e.preventDefault();
                if (!_this.hasClass('open')) {
                    settingMenuSp.show(_this, _id);
                } else {
                    settingMenuSp.hide();
                }
            }
        });
        $closeBtn.on('click', function(e) {
            e.preventDefault();
            settingMenuSp.hide();
        });
        settingMenuSp.resize();
    },
    show: function(_this, _id) {
        $('.mobile_control li a').removeClass('open');
        $('#tmp_wrapper').addClass('overlay');
        _this.addClass('open');
        settingMenuSp.resetText();
        _this.find('.nav_text').text('閉じる');
        $('.menu_sp').hide();
        $(_id).slideDown(300);
    },
    hide: function() {
        settingMenuSp.resetText();
        $('.menu_sp').slideUp(200);
        $('#tmp_wrapper').removeClass('overlay');
        $('.mobile_control li a').removeClass('open');
    },
    resetText: function() { 
        $('.navigation_link').find('.nav_text').html('検索<br />メニュー');
    },
    resize: function(){
        $(window).on('resize', function(){
            if($(window).width() > 640){
                $('#tmp_wrapper').removeClass('overlay');
            }
        });
    }
};
settingMenuSp.init();
```
# Hml
```html
 <ul id="tmp_hnavi_s">
      <li id="tmp_hnavi_rmenu">
          <a href="javascript:void(0);" class="sma_menu_open">
              <span class="menu_icon">&nbsp;</span>
              <span class="menu_text">メニュー</span>
          </a>
      </li>
  </ul>
```



# Css Icon Menu
```css
#tmp_header .sma_menu_open .icon {
    position: absolute;
    top: 16px;
    left: 50%;
    margin-left: 21px;
    width: 19px;
    height: 2px;
    background-color: #0c487b;
    color: #FFFFFF;
    z-index: 3;
    transition: all 0.2s ease 0s;
}
#tmp_header .sma_menu_open .icon::before,
#tmp_header .sma_menu_open .icon::after {
    content: "";
    width: 19px;
    height: 2px;
    left: 0px;
	background-color: #0c487b;
    color: #FFFFFF;
    position: absolute;
    top: 0px;
    z-index: 1;
    transition: all 0.2s ease 0s;
}
#tmp_header .sma_menu_open .icon::before {
	transform: translate(0px, -11px);
	top: 5px;
}
#tmp_header .sma_menu_open .icon::after {
	transform: translate(0px, 11px);
	top: -5px;
}
#tmp_sma_rmenu .active .icon::before {
	top: 0;
    transform: rotate(45deg);
    background-color: #FFFFFF;
}
#tmp_sma_rmenu .active .icon::after {
    transform: rotate(-45deg);
	background-color: #FFFFFF;
	top: 0;
}
#tmp_sma_rmenu .active .icon {
    background-color: transparent;
}
#tmp_sma_rmenu .sma_menu_open.active{
	background: #0c487b;
}
#tmp_sma_rmenu .active .text{
	color: #FFFFFF;
}
```