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

a();
```