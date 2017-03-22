# things-i18n-msg

## 동 component는 things-i18n-msg을 Things Framework에 맞게
## 수정하여 서버 및 local로 부터 언어데이타를 받아서 화면에 뿌려줌.
</br></br>



### **초기 데이터 벋아 오기**
things-i18n-src를 통하여 locale 소스 데이터를 받아 온다.

```html
    <things-i18n-src
      host="http://localhost:8080/components/things-i18n-msg/demo">
    </things-i18n-src>
```



*******

### **locale변경**

things-setting혹은 GlobalBehavior을 참조한 컴코넌트로 globals.locale에 대한 설정을 통하여 이루어 진다.
```js
    behaviors: [
      Things.GlobalBehavior
    ],
    ready: function(){
      this.set('globals.baseUrl',
              'http://localhost:8080/components/things-i18n-msg/demo');
      this.set('globals.locale', this.$.localeController.value);
    }
```

*******

**locale data 양식**
```js
  {
    "ko-KR":{
      "days": "일",
      "hours": "시간",
      "minutes": "분"
    }
  }
```

******
</br></br>

### **Fallback text**

만일 msgid를 key로 검색한 결과가 없으면 "fallback text"를 그대로 둔다.

```html
    <things-i18n-msg msgid="unknownmsgid">모를때 표현하는 정보</things-i18n-msg>
```


******
</br></br>

### **Data Binding**
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

### **Example 번수 치환:**

```html
    <things-i18n-msg auto
        msgid="msg"
        data-set='{"1":"전략사업","2":"홍길동"}'>
        부서 {1}의 {2}님이 오신걸 환영헙니다.
    </things-i18n-msg>
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
