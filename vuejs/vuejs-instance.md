# Vue Js Instance 
## 1. Data Option 
Data 옵션은 Vue인스턴스 내부에서 처리되지 않고 Data옵션에 주어진 객체와 Vue인스턴스 사이에 프록시에서 처리한다. 

프록시 처리가 되면 `vm.name`과 같이 사용할 수 있다. 
> Note 여러개 요소를 지정할 수는 없다. 여러개의 선택자로 연결되지 않고 최초 요소에만 연결된다. 

## 2. 메서드
동적으로 데이터를 계산하고 bind 한다는 점에서는 비슷하나 `계산형 속성(Computed Property)`과 내부 동작 방식에서 차이가 있다. `계산형 속성`은 종속된 값에 의해 결과값이 캐싱되고 `메서드`는 매번 실행을 한다. 
> Note `ECMA6` 에서 제공하는 `화살표 함수(Arrow Function)`은 사용이 불가하다. 

## 3. 관찰 속성(watch)
`계산형 속성(Computed Property)`처럼 하나의 데이터를 기반으로 다른 데이터를 변경할 필요가 있는 경우 `관찰 속성(watch)`을 사용한다. 
watch 옵션에 등록되는 것은 속성의 이름과 해당 속성이 변경되었을 때 호출되는 함수이다 함수는 인자를 전달 받는데 그 인자는 변경된 속성의 값 

## 4. Vue 인스턴스 라이플 사이클 
라이플 사이클 훅   | 설명 
-------------- | -----
beforeCreate | Vue 인스턴스가 생성 된 후 데이터에 대한 관찰 기능 및 이벤트 감시자 설정 이전에 호출 
created | 관찰 기능, 계산형 속성, 메서드, 감시자 설정이 완료된 후 호출
beforeMount | 마운트 시작 전 호출 
mounted | el에 vue 인스턴스 데이터가 마운트 후 호출 
beforeUpdate | 가상 DOM이 렌더링, 패치 이전 데이터 변경 전 호출 추가적 상태 변경은 가능하나 추가로 렌더링 하진 않는다. 
updated | 데이터 변경으로 가상 DOM이 다시 렌더링되고 패치 후 호출 
beforeDestory | Vue 인스턴스 가 제거되기 전 호출 
destoryed | Vue 인스턴스 제거된 후 호출 모든 디렉티브 바인딩이 해제, 이벤트 연결 모두 제거된다. 

![Image of Vue js Instance's Life cycle](../img/lifecycle.png)

## 5. 이벤트 객체 
이벤트를 처리하는 메서드는 첫번째 파라미터로 이벤트 객체를 전달 받는다. 
### 5.1 이벤트 객체의 주요 공통 속성
속성명 | 설명 
-----| ----
target | 이벤트 발생한 HTML 리턴
currentTarget | 이벤트리스너가 이벤트를 발생시키는 html 요소를 리턴 
path | 배열값 이벤트리스너가 이벤트를 발생 HTML 요소로부터 document, window 객체로까지 올라가는 경로를 나타냄 
bubbles | 현재의 이벤트가 버블링 일으키는 이벤트인지 여부를 리턴 
cancelable | 기본 이벤트를 방지할 수 있는지 여부를 리턴
defaultPrevented | 기본 이벤트가 방지되었는지 여부 리턴
eventPhase | 이벤트 흐름의 단계를 나타냄 
srcElement | IE에서 사용되던 속성으로 target과 동일한 속성

### 5.2 키보드 이벤트 관련 속성 