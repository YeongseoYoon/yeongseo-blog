---
title: '멱등성'
date: '2025-03-30T13:33:27.982Z'
summary: '멱이라는 글자 좀 이상하게 생김'
tags: ['DEV']
---

# 멱등성(Idempotency)이란?

단어 자체는 매우 생소합니다. 
200n년때 고등학생이셨다면 아마 이 단어를 보신 적이 있으셨을지 모르겠지만요(멱등함수라는 이름으로 고등학교 교과 개념에 등장했던 적이 있습니다.).

`멱등성`은 수학에서 등장하는 개념으로, 어떤 연산을 여러번 적용해도 결과가 달라지지 않는 성질을 의미합니다.
수학적으로 표현하면 함수 f에 대해 f(f(x)) = f(x)가 성립할 때, 함수 f는 `멱등`하다고 합니다. 이 간단한 개념은 현대 소프트웨어 개발의 여러 영역에서 중요한 역할을 합니다.

## HTTP에서의 멱등성

프론트엔드 개발자의 입장에서 멱등성이라는 개념은 `HTTP 메서드`에서 접할 수 있습니다.

우리가 자주 사용하는 HTTP 메서드는 다음과 같습니다.

- GET
- POST
- PUT
- DELETE
- PATCH

|메소드|멱등성|설명|
|---|---|---|
|GET|✅ 멱등함|리소스를 조회만 하므로 여러 번 호출해도 동일한 결과 반환|
|POST|❌ 멱등하지 않음|일반적으로 새 리소스를 생성하므로 호출할 때마다 결과가 달라짐|
|PUT|✅ 멱등함|리소스를 완전히 대체하므로 여러 번 호출해도 최종 상태는 동일함|
|DELETE|✅ 멱등함|리소스를 삭제한 후 다시 삭제해도 결과는 동일(리소스가 없는 상태)|
|PATCH|❌ 일반적으로 멱등하지 않음*|리소스의 일부만 수정하며, 구현에 따라 멱등할 수도 있음|

PATCH* 는 구현 방식에 따라 멱등할 수도 있습니다. 예를 들어 특정 값으로 설정하는 경우는 멱등하지만, 값을 증가시키는 경우는 멱등하지 않습니다.

### 안전한 메소드

`안전한 메소드`는 리소스를 변경하지 않는 메소드입니다. 즉, 리소스를 조회만 하므로 여러 번 호출해도 동일한 결과를 반환합니다.(수정하지 않습니다.)

다음과 같은 메소드들이 안전한 메소드입니다.

- GET
- HEAD
- OPTIONS


### 비안전한 메소드

`비안전한 메소드`는 리소스를 변경하는 메소드입니다. 즉, 리소스를 조회하는 것이 아니라 수정, 삭제, 생성 등을 합니다.

다음과 같은 메소드들이 비안전한 메소드입니다.

- POST
- PUT
- DELETE
- PATCH

그렇다면 표를 통해 비교해보겠습니다.

|메소드|안전성|멱등성|설명|
|---|---|---|---|
|GET|✅ 안전함|✅ 멱등함|리소스를 조회만 하므로 서버 상태 변경 없음|
|HEAD|✅ 안전함|✅ 멱등함|GET과 동일하지만 응답 본문 없이 헤더만 반환|
|OPTIONS|✅ 안전함|✅ 멱등함|리소스에 대한 통신 옵션 확인|
|PUT|❌ 안전하지 않음|✅ 멱등함|서버 상태를 변경하지만 여러 번 호출해도 결과 동일|
|DELETE|❌ 안전하지 않음|✅ 멱등함|서버 상태를 변경하지만 여러 번 호출해도 결과 동일|
|POST|❌ 안전하지 않음|❌ 멱등하지 않음|서버 상태 변경하며 여러 번 호출 시 결과도 달라짐|
|PATCH|❌ 안전하지 않음|❌ 일반적으로 멱등하지 않음*|서버 상태 변경, 구현에 따라 멱등할 수도 있음|

### 안전한 메소드와 멱등한 메소드의 차이점

안전한 메소드와 멱등한 메소드는 서로 다른 특성을 나타냅니다.

1. 모든 안전한 메소드는 멱등합니다 - 서버 상태를 변경하지 않기 때문에 자연스럽게 멱등성을 가집니다.
2. 모든 멱등한 메소드가 안전하지는 않습니다 - PUT, DELETE는 멱등하지만 서버 상태를 변경하므로 안전하지 않습니다.
3. 목적의 차이:
안전성: 클라이언트가 서버에 영향을 주지 않고 정보를 얻을 수 있는지 여부
멱등성: 반복 요청이 동일한 결과를 보장하는지 여부

## 멱등성 구현 방법

만약 결제하기와 같은 기능이 있다고 가정해 보겠습니다. 결제는 서비스에서 중요한 기능인 만큼 한 번만 트리깅 되어야 하는데요.
결제하기 버튼을 두 번 눌렀을 때 두 번 결제되는 것을 막도록 하려면 어떻게 해야 할까요?

이럴 때 멱등성을 구현하면 좋습니다.

1. 사용자 실수 방지: 느린 네트워크나 페이지 응답 지연으로 사용자가 버튼을 여러 번 클릭할 수 있습니다.
2. 중복 트랜잭션 방지: 결제와 같은 중요한 트랜잭션에서 중복 처리는 심각한 문제를 일으킬 수 있습니다.
3. 네트워크 오류 대응: 클라이언트가 서버 응답을 받지 못했을 때 안전하게 재시도할 수 있어야 합니다.

[토스](https://docs.tosspayments.com/blog/what-is-idempotency#예제로-이해하기)에서는 멱등성이 보장된 프로세스의 예시를 다음처럼 들고 있습니다.

```typescript
let idempotentKey = generateUUIDv4()
function async cancelPayment(idempotencyKey: string) {
  try {
    return await axios.post("https://myshop/cancel-payment",
      {
        orderId: UINQUE_ORDER_ID
        amount: 100,
      },
      {
        headers: {
          "Idempotency-Key": idempotentKey // 헤더에 멱등키를 추가합니다.
        }
      }
    )
  } catch(e) {
    if (e.name === "TIMEOUT") { // 타임아웃이 일어났을 때 같은 요청을 보낼 수 있습니다.
        return await cancelPayment(idempotencyKey)
    }
    console.error("ERROR")
  }
}
const response = await cancelPayment(idempotentKey);
```

클라이언트에서는 헤더에 멱등키를 추가해서 요청합니다.

```typescript
const idempotencyResponses = new Map();
let cancelReq = {
  orderId: req.body.orderId
  amount: req.body.amount,
};
let idempotencyKey = req.headers.idempotencyKey || null // 요청 헤더에서 멱등키를 가져옵니다.
// 멱등키가 있고 멱등 응답도 저장되어 있다면 실제 처리하지 않고 저장된 응답을 내보냅니다.
if (idempotencyKey != null && idempotencyResponses.has(idempotencyKey)) {
  const response = idempotencyResponses.get(idempotencyKey);
  return res.status(response.status).json(response);
};
const result = cancelProcessor.cancel(cancelReq); // 실제로 취소를 처리합니다.
// 멱등키가 있으면 멱등응답을 저장합니다.
if (idempotencyKey != null) {
  idempotencyResponses.set(idempotencyKey, result);
}
const responseBody = {
  message: `결제 취소 성공`,
};
return res.status(200).json(responseBody);
```
서버에서는 멱등키를 확인하고, 멱등키 DB에 멱등키와 매칭되는 요청 기록을 추가하고, 취소 처리에 성공했다면 성공 응답을 보냅니다.


## 멱등성의 한계와 주의사항
멱등성이 모든 문제를 해결해주는 만능 열쇠는 아닙니다.

다음과 같은 부분들을 고려하는 것에 있어서 리소스가 들 수 있습니다.

1. 상태 저장 비용: 멱등성 키와 이전 응답을 저장하는 것은 서버 리소스를 소모합니다.
2. 키 만료 정책: 멱등성 키를 얼마나 오래 보관할지 결정해야 합니다.
3. 복잡한 워크플로우: 다단계 트랜잭션에서는 멱등성 구현이 더 복잡해질 수 있습니다.
4. 외부 시스템 의존성: 외부 API가 멱등하지 않다면 완전한 멱등성 보장이 어려울 수 있습니다.

멱등성은 단순한 이론적 개념을 넘어, 실제 서비스의 안정성과 신뢰성을 높이는 중요한 설계 원칙입니다. 특히 금융 트랜잭션, 예약 시스템, 주문 처리와 같은 중요한 비즈니스 로직에서는 필수적으로 고려해야 할 요소입니다.

프론트엔드 개발자로서는 서버 API의 멱등성 특성을 이해하고, 이에 맞게 클라이언트 코드를 작성하는 것이 중요합니다. 특히 네트워크 불안정성이 있는 모바일 환경이나 중요한 트랜잭션을 다루는 경우, 멱등성을 고려한 설계는 사용자 경험을 크게 향상시킬 수 있습니다.

### ✏️ 출처
https://developer.mozilla.org/ko/docs/Glossary/Idempotent
https://docs.tosspayments.com/blog/what-is-idempotency#%EC%98%88%EC%A0%9C%EB%A1%9C-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0