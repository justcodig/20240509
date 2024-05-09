```sh
# git 초기화
git init

#  깃 원격 저장소 만들고
git config --global user.name "justcodig"
git config --global user.email "https://github.com/justcodig"

커밋하고 |
         

git remote add origin https://github.com/justcodig/20240509.git
git push -u origin master

# 깃에 올려서 일일 일 커밋을 습관화 하면 좋다

```

# 동기와 비동기 이벤트 루프

## 동기
> 직렬적으로 작업을 수행한다.

## 비동기
> 병렬젹으로 작업을 수행한다

## 스레드
> 일하는 사람의 숫자
> 혼자 일을 처리한다

> 내가 빨래를 널고 > 밥도 차리고 > 티비를 켜고


## 자바스크립트의 비동기 처리
1. web api == DOM == DOM, settmeout
2. task Queue == 이벤트 발생후 호출되어야할 콜백이 쌓이는 공간 Evnet loop가 정한대로 순서대로 기다린다.(콜백 큐)
3. Evnet loop == 이벤트 발생하고 호출될 콜백 함수를 관리 순서를 결정해준다


```js
function a(){
console.log("안녕");
console.log("안녕2");
console.log("안녕3");
}
setTimeout(()=>{
    console.log("안녕");
},1000) // 1초뒤에 실행할 함수
setTimeout(()=>{
    console.log("안녕");
},500) // 0.5초뒤에 실행할 함수

a();
```

## 이벤트 루프
> 정한 순서대로 나열되어있는 콜백함수들을 콜스택이 비워지면 순서대로 호출해서 실행한다. `콜백 큐`
> 실행 순서를 정해준다
> 비동기적 자바스크립트 처리 코드가 종료되지 않아도 대기하지않고 다음 코드줄을 실행하는 자바스크립트 특성(싱글 스레드)
> 이벤트 루프 특성을 사용한다 비동기 처리를 위해서


### setTimeout
> 콜스택에 쌓여있는 모두 처리하고 호출을 하기때문에 정확하지 않다

### 비동기 처리
> 서버로 데이터 요청을 보내고 응답을 받고 처리해야 하는 코드를 기다리고 처리하고
> 웹페이지의 다른 코드들은 우리가 서버의 데이터를 받는동안 웹페이지가 안뜨거나 다른 코드들이 멈춰 있을 수 없기때문에


## promise 객체
> 비동기 처리를 할때 사용하고
> 대기, 성공, 실패의 반환값과 메서드를 가지고 있는 객체
```js
const  promise = new Promise((res,rej)=>{
    // 비동기 처리 구문
    // setTimeout
    if("성공"){
        res("성공했어");
    }
    if{
        rej("실패했어");
    }

}); // promise 객체 생성
// 인자로 생성자 함수에 콜백 함수를 전달한다
// res 성공의 결과를 반환해줄 함수(첫번째 매개변수)
// rej 실패의 결과를 반환해줄 함수(두번째 매개변수)

promise.then((result) => {console.log(result)}); // 비동기 처리를 한뒤에 성공 결과를 반환한다.
promise.catch((error) => {console.log(error)}); // 비동기 처리를 한뒤데 실패 결과를 반환한다.

const  promise = new Promise((res,rej)=>{
    // 비동기 처리 구문
    // setTimeout
    
     setTimeout(() => {
        res("성공했어");
    }, 1000);


});



const num =10;
const promise2 = new Promise((res,rej) => {
    if(num > 5) {
        res("num이 5보다 크다");
    }else {
        rej("num이 5보다 작아")
    }
});

promise2.then((result) => {console.log(result)}).catch((error) => {console.log(error)})
```