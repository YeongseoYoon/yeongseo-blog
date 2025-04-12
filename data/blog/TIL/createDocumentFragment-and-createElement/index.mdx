---
title: 'createDocumentFragment vs createElement'
date: '2025-04-12T13:33:27.982Z'
summary: 'DOM DOM 댄스'
tags: ['JavaScript']
---

DOM(Document Object Model) 조작은 웹 개발의 핵심 부분입니다. 요소를 생성하고 변경하며 문서에 추가하는 과정은 사용자 인터페이스를 구축하는 기본 작업입니다. JavaScript에서는 주로 `createElement` 메서드를 사용해 요소를 생성합니다.

```js
const div = document.createElement('div');
```

그러나 많은 요소를 처리할 때는 `createDocumentFragment`가 성능적으로 유리할 수 있습니다. 이 글에서는 브라우저 렌더링 과정을 살펴보고, `createElement`와 `createDocumentFragment`의 차이점 및 성능 특성을 리플로우 관점에서 비교해 보겠습니다.


# 브라우저 렌더링 과정

브라우저가 HTML, CSS, JavaScript 코드를 읽고 화면에 렌더링하는 과정은 다음과 같습니다.

1. 브라우저가 HTML을 파싱하여 DOM 트리를 생성합니다.
2. 브라우저가 CSS를 파싱하여 CSSOM 트리를 생성합니다.
3. DOM 트리와 CSSOM 트리를 결합하여 렌더 트리를 생성합니다.
4. 렌더 트리를 기반으로 레이아웃(리플로우), 페인트(리페인트)가 발생합니다.
5. 페인팅된 여러 레이어를 합쳐 최종 화면을 만드는 컴포지팅이 일어납니다.

<figure>
<img src="/static/images/브라우저-렌더링-과정.svg" alt="브라우저 렌더링 과정" />
<figcaption>브라우저 렌더링 과정</figcaption>
</figure>

이 과정에서 성능에 가장 큰 영향을 미치는 단계는 `레이아웃(리플로우)`과 `페인트(리페인트)`입니다. 
특히 `리플로우`는 계산 비용이 높은 작업으로, 최소화하는 것이 웹 성능 최적화의 핵심입니다.


# createElement vs createDocumentFragment

JavaScript에서 DOM을 동적으로 조작할 때 주로 사용하는 두 가지 방법은 `createElement`와 `createDocumentFragment`입니다. 이 두 메서드는 어떻게 다르고, 브라우저 렌더링 과정에 어떤 영향을 미칠까요?

## createElement
`document.createElement()`는 지정된 HTML 태그 이름의 새 요소를 생성합니다.

```js
const newDiv = document.createElement('div');
newDiv.textContent = '새로운 요소입니다';
document.body.appendChild(newDiv);
```

이 방식으로 DOM에 요소를 추가하면

1. 새 요소가 생성됩니다
2. 요소가 DOM 트리에 추가됩니다
3. 브라우저는 DOM 트리 변경을 감지하고 리플로우와 리페인트를 수행합니다

여러 요소를 추가하는 경우 각 요소마다 위 과정을 반복합니다.

```js
const container = document.getElementById('container');
for (let i = 0; i < 1000; i++) {
  const div = document.createElement('div');
  div.textContent = `항목 ${i}`;
  container.appendChild(div);
}
```
이 코드는 루프가 1000번 반복되며, 각 반복마다 DOM이 수정되고 잠재적으로 리플로우가 발생할 수 있습니다. 
브라우저는 일부 DOM 변경을 일괄 처리하려고 하지만, 여전히 다수의 리플로우가 발생할 가능성이 높습니다.


## createDocumentFragment

`document.createDocumentFragment()`는 메모리에만 존재하는 경량 DOM 컨테이너를 생성합니다.

```js
const fragment = document.createDocumentFragment();
for (let i = 0; i < 1000; i++) {
  const div = document.createElement('div');
  div.textContent = `항목 ${i}`;
  fragment.appendChild(div);
}
document.getElementById('container').appendChild(fragment);}
```

이 방식으로 DOM에 요소를 추가하면

1. 메모리 내 DocumentFragment 객체를 생성합니다.
2. 모든 요소를 이 Fragment에 추가합니다. (실제 DOM에는 영향을 주지 않음)
3. 모든 요소가 준비되면 Fragment를 한 번에 DOM에 추가합니다.
4. Fragment 자체는 DOM에 추가되지 않고, 그 내용만 DOM에 병합됩니다.
5. 리플로우와 리페인트가 단 한 번만 발생합니다.

# 성능을 비교해보자!
위에서 살펴본 두 방식의 성능 차이를 직접 측정해보기 위해 간단한 실험을 해보겠습니다.

```js
// 직접 appendChild 테스트
function testCreateElement(itemCount) {
  const startTime = performance.now();
  
  for (let i = 0; i < itemCount; i++) {
    const li = document.createElement('li');
    li.textContent = `Item ${i + 1}`;
    list1.appendChild(li);
  }
  
  const endTime = performance.now();
  return endTime - startTime;
}

// DocumentFragment 테스트
function testDocumentFragment(itemCount) {
  const startTime = performance.now();
  
  const fragment = document.createDocumentFragment();
  
  // Fragment에 요소 추가 (DOM에 직접 추가하지 않음)
  for (let i = 0; i < itemCount; i++) {
    const li = document.createElement('li');
    li.textContent = `Item ${i + 1}`;
    fragment.appendChild(li);
  }
  
  // Fragment를 DOM에 한 번에 추가
  list2.appendChild(fragment);
  
  const endTime = performance.now();
  return endTime - startTime;
}
```


## 테스트 결과
<figure>
<img src="/static/images/performance-createElement-and-createDocumentFragement.png" alt="createElement와 createDocumentFragment 성능 비교" />
<figcaption>createElement와 createDocumentFragment 성능 비교</figcaption>
</figure>

| 요소 수 | createElement (ms) | createDocumentFragment (ms) |
|---------|-------------------|---------------------------|
| 10      | 0.10              | 0.10                      |
| 1,000   | 2.60              | 2.10                      |
| 5,000   | 8.50              | 7.60                      |
| 10,000  | 12.80             | 9.40                      |


테스트 결과에서 볼 수 있듯이, 요소 수가 증가할수록 createDocumentFragment의 성능 이점이 더 뚜렷해집니다.

1. 적은 요소 수(10개): 두 방식 간의 성능 차이가 거의 없습니다. 매우 적은 양의 DOM 조작에서는 어떤 방식을 사용해도 무방합니다.
2. 중간 요소 수(1,000개): createDocumentFragment가 약 19% 더 빠릅니다.
3. 많은 요소 수(5,000개): createDocumentFragment가 약 11% 더 빠릅니다.
4. 대량 요소 수(10,000개): createDocumentFragment가 약 27% 더 빠릅니다. 요소 수가 증가함에 따라 성능 차이가 더 커집니다.

### 성능 차이의 원인
`createDocumentFragment`가 성능 이점을 갖는 주된 이유는 리플로우 횟수의 감소입니다.

1. `createElement` + 직접 `appendChild`
- 각 요소를 DOM에 추가할 때마다 잠재적으로 리플로우가 발생할 수 있습니다.
- 브라우저는 일부 변경을 일괄 처리하지만, 여전히 여러 번의 리플로우가 발생합니다.


2. `createDocumentFragment`
- Fragment에 요소를 추가할 때는 DOM에 영향을 주지 않으므로 리플로우가 발생하지 않습니다.
- Fragment를 DOM에 추가할 때 단 한 번의 리플로우만 발생합니다.
- 요소가 많을수록 이러한 최적화의 효과는 더 커집니다.

이 실험을 통해 `createDocumentFragment`가 많은 DOM 요소를 처리할 때 성능 이점을 제공한다는 것을 확인했습니다. 10,000개 요소를 처리할 때는 약 27%의 성능 향상을 보였습니다.
이러한 성능 최적화의 핵심은 리플로우 횟수의 최소화입니다. `createDocumentFragment`는 메모리 내에서 변경사항을 준비한 후 단 한 번의 DOM 업데이트로 모든 변경을 적용하므로 브라우저 렌더링 엔진의 부담을 크게 줄여줍니다.
현대 웹 프레임워크는 이미 내부적으로 이와 유사한 최적화를 수행하지만, 바닐라 JavaScript로 웹 애플리케이션을 개발하거나 레거시 코드를 최적화할 때는 `createDocumentFragment`를 활용하는 것이 성능 향상에 큰 도움이 될 것입니다.

### ✏️ 출처
https://developer.mozilla.org/ko/docs/Web/API/Document/createDocumentFragment<br/>
https://developer.mozilla.org/ko/docs/Web/API/Document/createElement<br/>
https://johnresig.com/blog/dom-documentfragments/<br/>
