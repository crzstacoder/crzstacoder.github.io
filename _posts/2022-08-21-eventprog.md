---
published: true
title: "Javascript에서의 이벤트 기반 프로그래밍"
excerpt: "node.js, express.js를 쓰다가 알아버린.."

tags:
    - [Queue, javascript, Server]
categories:
    - cs

toc: true
toc_sticky: true

date: 2022-08-21
last_modified_at: 2022-08-21
---

**본 내용은 고등학교 3학년 초짜 개발자의 공부노트이므로, 틀린 정보일 수 있습니다.**
  
  

## **싱글 스레드에서의 이벤트 기반이란?**
 이벤트가 생성되었을때, 이벤트를 인식하고 그 이벤트를 하나하나 처리하는 방법이다.  

#  
## **싱글 스레드의 문제점**
제일 큰 문제점은 사실 '시간'이다.  
**싱글 스레드**에서는 한번에 여러개의 이벤트가 처리되지 않도록  
이벤트가 처리되는 과정에서 **I/O blopping**을 하여 시스템을 잠시 멈춘다.  
이렇게 대기하고 있는 상태에서 지속적으로 다른 이벤트들이 쌓이게 되고,  
시간적인 효율에서 치명적인 문제가 생긴다.
   

 예를 들어, http로 요청을 보내고 응답을 받아야 하는데,  
 응답을 받고 처리하기까지의 과정에서 대기시간이 너무나도 길어진다는 것이다.

  
  
 ## **이벤트 기반 프로그래밍 도입!**
따라서 응답이 필요한 이벤트는...  
> 요청을 보내고,  
다른 이벤트들을 처리하다가,  
응답이 오면 message queue에 콜백함수를 사용하여 넣고,  
message queue에 쌓인 이벤트들을 차례대로 처리할 수 있게 한다.

![image](/assets/image/1.png)  
<cite><h5> [출처] Minsu's Dev Log</cite> --- 메시지 큐와 이벤트 루프</h5>

이것이 바로 js의 동작구조이다.  
event loop는 지속적으로 message queue(callback queue)에 쌓인 이벤트들을 감지하고,  
응답하기까지 시간이 걸리는 이벤트들은 callbackfunction을 이용해 message queue에 쌓는다.





