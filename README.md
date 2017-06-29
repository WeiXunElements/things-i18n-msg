# things-i18n-msg

## The component modifies things-i18n-msg to match Things Framework and receives the language data from the server and local and displays it on the screen.
</br></br>



### **Get initial data**
It gets locale source data through things-i18n-src.

```html
    <things-i18n-src
      host="http://localhost:8080/components/things-i18n-msg/demo">
    </things-i18n-src>
```



*******

### **Change locale**

This is a component that refers to things-setting or Global Behavior and is changed through configuration for globals.locale.

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

**Locale data form**
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

If there is no result of retrieving msgid by key, it keeps "fallback text".

```html
    <things-i18n-msg msgid="unknownmsgid">Unknown information</things-i18n-msg>
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

### **Example Variable substitution**

```html
    <things-i18n-msg auto
        msgid="msg"
        data-set='{"1":"Strategic Business","2":"John"}'>
        Welcome {2} from department {1}.
    </things-i18n-msg>
```

### **Using JS**

```js
  // Label acquisition
  Things.DataGlobal.t('label.serial');
  // Variable substitution
  var dataSet = {"1":"Strategic Business","2":"John"};
  Things.DataGlobal.t('text.serial',dataSet);
```

## Dependencies

Element dependencies are managed via [Bower](http://bower.io/). You can install that via:

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
