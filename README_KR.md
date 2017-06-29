# things-i18n-msg

## 해당 component는 things-i18n-msg를 Things Framework에 맞게 수정한 후 서버 및 local로부터 언어 데이터를 받아서 화면에 뿌려준다.
</br></br>



### **초기 데이터 받아오기**
things-i18n-src를 통하여 locale 소스 데이터를 받아온다.

```html
    <things-i18n-src
      host="http://localhost:8080/components/things-i18n-msg/demo">
    </things-i18n-src>
```



*******

### **locale 변경**

이는 things-setting 혹은 Global Behavior를 참조한 컴포넌트로, globals.locale에 대한 설정을 통하여 변경된다.
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

만약 msgid를 key로 검색한 결과가 없으면 "fallback text"를 유지한다.

```html
    <things-i18n-msg msgid="unknownmsgid">모를 때 표현하는 정보</things-i18n-msg>
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

### **Example 변수 치환**

```html
    <things-i18n-msg auto
        msgid="msg"
        data-set='{"1":"전략사업","2":"홍길동"}'>
        부서 {1}의 {2}님이 오신 걸 환영합니다.
    </things-i18n-msg>
```

### **JS 사용**

```js
  // 라벨 획득
  Things.DataGlobal.t('label.serial');
  // 변수 치환
  var dataSet = {"1":"전략사업","2":"홍길동"};
  Things.DataGlobal.t('text.serial',dataSet);
```

## Dependencies

element의 종속성은 [Bower](http://bower.io/)를 통해 관리되며, 아래의 방법을 통해 설치할 수 있다.

    npm install -g bower

다음, element의 종속성을 다운로드한다.

    bower install


## Playing With Your Element

element를 독립적으로 처리하려면 [Polyserve](https://github.com/PolymerLabs/polyserve)를 사용하여 element의 bower 의존성을 유지하도록 하며, 이는 아래의 방법을 통해 설치할 수 있다.

    npm install -g polyserve

그리고, 아래의 방법을 통해 실행할 수 있다.

    polyserve

element를 실행한 경우, `things-i18n-msg`가 디렉토리 이름으로 포함되어 있는 `http://localhost:8080/components/things-i18n-msg/`를 통해 이를 미리 확인할 수 있다. 
