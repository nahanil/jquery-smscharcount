# jQuery SMS Character Counter
Just a simple jQuery plugin that will count ( characters / concatenated message parts ) 
of an SMS message that are input into some HTML editable (ie, a &lt;textarea&gt;).

## Usage
```html
<!-- Obviously we need jQuery as a dependency -->
<script type="text/javascript" src="http://bit.ly/jqsource"></script>
<!-- Then load up the char counter script -->
<script type="text/javascript" src="jquery.smscharcount.js"></script>
```

Then somewhere in our code

```js
$(function(){
  $('textarea#sms_body').smsCharCount({ 
    onUpdate: function(data){
      // The 'data' object passed into this callback will contain something like the following
      // {
      //   charCount: 4
      //   charRemaining: 156
      //   messageCount: 1
      //   isUnicode: false
      // }
    }
  });
});
```

## Example
... Soon ...
