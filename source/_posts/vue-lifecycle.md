---
title: 뷰 라이프사이클(3)
date: 2019-12-18 21:46:01
tags: vue
category: 
- vue
- vue 기본문법
---

#### 설명
vue는 여러 종류의 라이프 사이클을 가집니다. 각각의 라이프 사이클 마다 사용자 정의 로직을 실행할수 있는 라이크 사이클 훅을 호출 합니다.

<br>

#### 라이프사이클 훅의 종류


##### 1. beforeCreate


인스턴스를 생성 후 가장 먼저 실행되는 라이프 사이클 단계입니다. 이 단계에서는 data및 methods 속성이 정의되어 있지 않습니다.

<br>

##### 2. created

beforeCreate 다음 실행 단계로써 data 및 methods 속성에 접근이 가능합니다. 아직까지 화면에 부착전이기 때문에 돔 요소에 접근은 불가능합니다.

##### __사용용도__ 

> 보통 이 단계에서 서버에서 데이터를 요청하여 받아오는 로직을 수행하기에 좋습니다 
> 이 단계부터 data나 속성 등에 접근이 가능하기 때문에 화면에 부착하기 전 data등의 속성에 값을 변경 시키는 등의 작업을 이 단계에서 진행합니다.

<br>

##### 3. beforeMount


화면에 인스턴스를 부착하기 전 단계입니다. 

##### __사용용도__

> render 함수가 호출 되기 직전의 로직을 추가하기에 좋습니다.

<br>

##### 4. mounted


화면에 인스턴스가 부착되고 난 후에 호출 되는 단계입니다. 이때 부터 template 속성에 정의한 화면요소에 대한 접근이 가능합니다. 돔에 인스턴스가 부착되자마자 바로 호출 되는 단계라서 하위 컴포넌트나 외부 라이브러리에 의해 추가 된 화면 요소들이 HTML 코드로 변환되는 시점과 다를수있습니다.

##### __사용용도__

> 이 단계부터 template 속성의 값이 화면에 부착되었기 때문에 돔에 접근을 할때 사용합니다.

<br>

##### 5. beforeUpdate
 : 인스턴스에 정의 된 속성이 변경되어 돔으로 화면을 다시 그리기 전 단계입니다.

아직 화면에 그려지기 전에 변경 된 데이터에 접근이 가능합니다. 이때 값을 변경하는 로직을 넣어 렌더링이 발생하더라도 트리거 되지 않습니다.

<br>

##### 6. updated 

변경 된 데이터가 화면으로 그려지고 난 후 실행되는 단계입니다. 이 단계에서 값을 변경 할 경우 무한루프에 빠질 수 있습니다.

##### __사용용도__

인스턴스의 속성 값이 변경 될때 값을 변경하는 로직을 실행해야 한다면 beforeUpdate에서 작성을 하고 updated에서는 속성 값이 변경 될때 화면 구성요소와 관련 된 작업을 이단계에 넣습니다.

<br>

##### 7. beforeDestory


뷰 인스턴스가 파괴되기 직전에 호출 되는 단계입니다.

##### __사용용도__

뷰 인스턴스의 데이터를 삭제하기 좋은 단계입니다. 이벤트버스를 사용 할때 해당 컴포넌트가 삭제가 되어도 그대로 남아 있어서 이벤트가 여러번 실행되는 경우가 발생합니다. 해당 컴포넌트에서 이벤트버스 $on을 사용했다면 여기에서 $off 추가합시다.

<br>

##### 8. destroyed


뷰 인스턴스가 파괴되고 난 후 호출되는 단계입니다.                    

```html
new Vue({
    el: '#app',
    beforeCreate() {

    },

    created() {

    },

    beforeMount() {

    },

    mounted() {

    },

    beforeUpdate() {

    },

    updated() {

    },

    beforeDestroy() {

    },

    destroyed() {

    }
})
```

![뷰 라이프 사이클](https://user-images.githubusercontent.com/42727909/55003776-595bb700-501c-11e9-84b8-3a4acfc5465c.png)
{% blockquote https://kr.vuejs.org/v2/guide/instance.htm 인용 %}
{% endblockquote %}