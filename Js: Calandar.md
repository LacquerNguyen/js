# Calandar
```javascript
   $(".start_date").each(function() {
        var input = $(this).pickadate({
        editable: true,
        today: '',
        clear: '',
        formatSubmit: 'yyyy/mm/dd',
        format: 'yyyy/mm/dd',
        monthsFull: [ '1月', '2月', '3月', '4月', '5月', '6月', '7月', '8月', '9月', '10月', '11月', '12月' ],
        weekdaysShort: [ '日', '月', '火', '水', '木', '金', '土' ],
    });
    var picker = input.pickadate('picker');
    $(this).off('click focus');

    $(this).closest('.item_calendar').find('.button_date').on('click', function(e) {
      if (picker.get('open')) { 
        picker.close()
      } else {
        picker.open()
      }
      
      return false;   
    });
})
```
