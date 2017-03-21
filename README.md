# things-i18n-msg

## 동 component는 things-i18n-msg을 Things Framework에 맞게
## 수정하여 서버 및 local로 부터 언어데이타를 받아서 화면에 뿌려줌.
</br></br>

### locale변경
main page 혹은 things-setting으로 dataGlobals에 Base Url 및 locale을 수정하여 notifyPath를 해 준다.:
```js
  window.addEventListener('WebComponentsReady', function() {
    _thingsGlobalBehaviorInstances[0].set('globals.baseUrl', 'http://localhost:8080/components/things-i18n-msg/demo');
    _thingsGlobalBehaviorInstances[0].set('globals.locale', 'en');
  });
```

<b>데이타 격식 및 Path</b>

<b> 격식 :</b>
```js
{
  "localeName" : {
    key:value
  }
}
```

<b>예</b>
```js
  {
    "ko-KR":{
      "days": "일",
      "hours": "시간",
      "minutes": "분"
    }
  }
```

<b> Path :</b>

Local에 Message.Json파일이 있을 경우 root/terminologies/resource아래에 {{locale}}.json형태로 저장되어 있어야 한다.

<b>Example</b> - 전체 `<things-i18n-msg>` instances에 URL경로 변경을 알리며 데이터를 Refresh한다.:

```js
    _thingsGlobalBehaviorInstances[0].set('globals.baseUrl', 'http://localhost:8080/components/things-i18n-msg/demo');
```

<b>Example</b> - 특수한 태그에서 해당 태그에만의 locale파일 위치를 지정할 수 있다.:

```html
    <things-i18n-src src-url="path/to/locales">fallback text</things-i18n-src>
```
<b>Note:</b> 하지만 동일한 locale에 대하여서는 데이타를 한번만 받아 온다.


******

</br></br>

### Fallback text

만일 msgid를 key로 검색한 결과가 없으면 "fallback text"를 그대로 둔다.

    <i18n-msg msgid="unknownmsgid">fallback text</i18n-msg>


******
</br></br>
### With Data Binding
```html
    <template is="dom-bind">
        <things-i18n-msg msgid="days" msg="{{days}}"></things-i18n-msg>
        <p>Example of updating an attribute:
            <input id="input" placeholder="[[days]]">
        </p>
    </template>
```

******
</br></br>
### Example of updating an attribute with getMsg() method:
```html
    <input id="input" placeholder="Days">
    <script>
      var el = document.createElement('things-i18n-msg');
      el.msgid = 'minutes';
      document.querySelector('#dynamic').appendChild(el);
    </script>
```


## Dependencies

Element dependencies are managed via [Bower](http://bower.io/). You can
install that via:

    npm install -g bower

Then, go ahead and download the element's dependencies:

    bower install


## Playing With Your Element

If you wish to work on your element in isolation, we recommend that you use
[Polyserve](https://github.com/PolymerLabs/polyserve) to keep your element's
bower dependencies in line. You can install it via:

    npm install -g polyserve

And you can run it via:

    polyserve

Once running, you can preview your element at
`http://localhost:8080/components/things-i18n-msg/`, where `things-i18n-msg` is the name of the directory containing it.
