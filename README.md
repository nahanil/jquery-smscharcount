# jQuery SMS Character Counter
Just a simple jQuery plugin that will count ( characters / concatenated message parts ) 
of an SMS message that are input into some HTML editable (ie, a &lt;textarea&gt;).

## Why?
You might be thinking "Why not just use ```myMessageString.length```?"

There are a few nuances in the way that SMS messages, and the parts that long messages are split into, are counted.
For example, a single SMS may contain 160 characters in [the default 7-bit GSM encoding](http://en.wikipedia.org/wiki/GSM_03.38#GSM_7-bit_default_alphabet_and_extension_table_of_3GPP_TS_23.038_.2F_GSM_03.38). Several characters in this 7-bit encoding are escaped, ie, they take up the space of 2 characters. These characters are ```{}[]\|^~€```.

Other characters outside the default 7-bit character set can be used (你好！), and will generally be encoded in [UCS-2](http://en.wikipedia.org/wiki/UCS-2). These messages are limited to 70 characters.

In the case of messages over 160 characters long, the message is broken into parts which are delivered seperately. Each of these message parts requires a small header to be attached to it so that it can be pieced back together on the receiving end. This means that each 'part' of a standard concatenated / multi-part message can only contain 153 characters (with the other 7 being used for the header). Messages with characters outside the default character set are limited to 70 characters normally, and 67 when part of a concatenated message.

This little library ***attempts*** to take all of these considerations into account when counting the size of the raw text it is given.

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
