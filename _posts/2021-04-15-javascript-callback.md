---
title: \[JavaScript\] Callback
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
tags:
- JavaScript
toc: true
toc_sticky: true
markdown: kramdown
highlighter: rouge
categories:
- JavaScript Study
---

# Callback 
* JavaScript 비동기 동작을 위한 가장 기본적인 개념
* 인자로 다른 함수에 전달되는 함수로, 외부 함수 내에서 호출되어 루틴(routine) 또는 작업(action)을 완료

## 필요한 이유
JavaScript 코드는 기본적으로 순차적으로 동작하나, 특정 코드 실행되기 위해 다른 코드가 먼저 수행되어야 하는 경우도 있고 순차적으로 실행되지 않는 경우도 있다. 
예를 들어 A, B, C라는 작업이 처리되는데 있어서, 작업간에 처리 순서가 상관이 없는데 A라는 작업이 모두 처리될때까지 기다릴 필요는 없을 것이다. 
이러한 경우 A 작업이 처리하면서 B, C 작업도 처리되도록 하는 것을 비동기 프로그래밍(asynchronous programming)이라고 한다. 

만약 위의 상황에서 C 작업이 처리된 후에 B 작업이 처리되도록 하고 싶다고 하자. 
이때 C 작업이 처리 된후에 B 작업에게 C 작업이 끝났다는 것을 알리는 동작을 수행하는것이 콜백이라고 할 수 있다. 
단순하게 생각해서 특정 작업이 끝났다는 것을 알기 위해, 작업이 끝났는지 주기적으로 체크하는 것보다는 작업을 진행하고 있는 주체가 자신의 작업이 끝난 것을 자신이 
끝나길 대기중인 작업에게 알려주는게 더 효율적일 것이다. 특히나 JavaScript 특성상 전통적으로 사용자 인터페이스의 기능을 구현해온 프로그래밍 언어로 이벤트 기반 
및 비동기 처리 무척 중요한것 같다. 거두절미하고 JavaScript에서 비동기를 구현하기 위한 기본적인 개념으로 콜백은 중요하다.

## 처리 방식 

### Timer
* 일정 시간이 경과했을 때 특정 코드를 실행하는 경우

JavaScript에서 타이머(Timer)를 구현하기 위해서는 `setTimeout(function, milliseconds)` 함수를 사용한다. 
* `function`: 타이머가 만료된 뒤 실행되는 함수
* `milliseconds`: 함수를 실행시키기 전에 기다려야하는 시간(단위: ms)을 지정

`setTimeout`는 지정한 함수를 콜백 방식으로 호출하며, 인자(argument)를 전달하지 않는다.  
일정 주기를 기준으로 반복해서 특정 코드를 실행하는 경우 `setInterval(function, milliseconds)` 함수를 사용한다.  

### Event
* 사용자가 동작을 수행하면 사용자의 동작에 응답하는 경우

JavaScript로 작성되는 프로그램은 보편적으로 이벤트 기반(event driven)으로, 대부분의 기능이 미리 결정된 계산을 하는것 보다는, 사용자와 상호작용하여 사용자의 동작에 응답한다.  
JavaScript 프로그램은 지정된 타입의 이벤트에 대한 콜백 함수를 등록하고, 브라우저는 해당 타입의 이벤트가 발생할때마다 함수를 호출한다.  
이러한 콜백 함수는 이벤트 핸들러(Event Handler) 또는 이벤트 리스너(Event Listener)라고 하며 `addEventListener()`에 등록된다.  

# 참고자료
* [JavaScript Callback Functions](https://www.freecodecamp.org/news/javascript-callback-functions-what-are-callbacks-in-js-and-how-to-use-them/)
* [JavaScript The Definitive Guide](https://www.amazon.com/JavaScript-Definitive-Most-Used-Programming-Language/dp/1491952024/ref=sr_1_1?dchild=1&keywords=JavaScript+The+Definitive+Guide&qid=1618483518&s=books&sr=1-1)
* [JavaScript Timing Events](https://www.w3schools.com/js/js_timing.asp)
* [MDN Web Docs - Callback function](https://developer.mozilla.org/en-US/docs/Glossary/Callback_function)
* [MDN Web Docs - WindowTimers.setTimeout()](https://developer.mozilla.org/ko/docs/Web/API/WindowOrWorkerGlobalScope/setTimeout)
* [MDN Web Docs - EventTarget.addEventListener()](https://developer.mozilla.org/ko/docs/Web/API/EventTarget/addEventListener)