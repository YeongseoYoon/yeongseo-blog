---
title: 'Playwright 넌 누구냐'
date: '2024-01-19T06:29:32.468Z'
summary: '가면인간'
tags: ['TEST', 'PLAYWRIGHT']
---

# Playwright이란

<img src="https://github.com/YeongseoYoon/yeongseo-blog/assets/86523545/dd096782-6a2d-4cf4-a574-4e54df40f812" />
[Playwright](https://playwright.dev/docs/intro)이란 마이크로소프트에서 개발한 오픈 소스 라이브러리로(정확히는
puppeteer팀이 마이크로소프트 팀으로 들어가 개발), 웹 브라우저를 자동화하기 위한 것입니다. <br /> Chromium,
WebKit, 그리고 Firefox를 지원합니다.

## Cypress vs Playwright

저희 회사는 E2E테스트에서 기존에는 `Cypress`를 사용하다 `Playwright`로 전환해 사용했는데 이유는 다음과 같았습니다.

1. 같은 조건(Headless 모드, 1개의 워커)에서 테스트 코드를 실행할 경우 Cypress보다 Playwright가 우세한 속도를 보였습니다.
2. 워커 수를 늘려 병렬로 진행시 Cypress는 유료로 진행해야 합니다.
3. Playwright은 지원하는 언어에 대한 순수 문법을 제공하는 반면(await 등), Cypress는 자체 문법을 가집니다.
4. Playwright이 요소를 찾을 때 조금 더 엄격한 문법을 가집니다. 따라서 Cypress에 비해 더욱 명확하게 요소를 지시해야 합니다.

<img src="https://github.com/YeongseoYoon/yeongseo-blog/assets/86523545/64632df0-645a-477a-a5bf-97dd8b0a64e0" />
Cypress가 아직까지는 많은 점유율을 가지고 있고 그에 따라 큰 커뮤니티를 가지고 있어 정보의 공유가 원활하다는
점, 사용이 조금 더 직관적이라는 점이 있지만 Playwright 또한 점유율을 조금씩 가져가고 있고 문법이 자바스크립트와
거의 비슷해 러닝커브가 적다는 점을 고려했습니다.

## Playwright 사용법

물론 [Playwright 공식문서](https://playwright.dev/docs/intro)에서도 설명하고 있는 내용들입니다만 제가 사용하는 방식을 공유해보려 합니다.

### 1. 사용할 worker 지정하기

Playwright에서는 병렬 테스트를 위해 논리 CPU 코어의 비율을 지정하여 병렬로 실행할 작업자 프로세스의 최대 수를 설정할 수 있습니다.

또한 CI 환경에서의 워커수를 지정할 수 있습니다.

```ts
const config = defineConfig({
  workers: process.env.CI ? 2 : '50%',
});
```

### 2. api response를 intercept하기

비용상의 문제라던가 하는 이유로 상황에 따라서 테스트를 위한 서버가 존재하지 않는 경우가 있을 겁니다. 그런 경우 `Response Interception`을 이용하여 테스트 할 수 있습니다.

우선, 해당 api로 요청이 들어오면 응답으로 던져줄 mock data를 구성합니다.

```ts
const myPizza = {
  id: 23,
  type: 'PIZZA',
  name: '존스 페이보릿',
};
```

그리고 api를 intercept하기 위한 함수를 작성합니다.

```ts
const getPizza = async (page: Page) => {
  await page.route(`/api/pizza/22`, async (route) => {
    const body = JSON.stringify(myPizza);
    await route.fulfill({ body });
  });
};
```

위 코드처럼 api 요청에 해당하는 응답값을 내가 원하는 값으로 지정해 보내줄 수 있습니다.

### 3. 파일 업로드 테스트 하기

가끔 파일 업로드를 테스트할 필요가 있을 때가 있습니다. 이런 경우

```ts
await fileUploaderInput.setInputFiles({
  name: 'file.txt',
  mimeType: 'text/plain',
  buffer: Buffer.from('this is test'),
});
```

위와 같이 setInputFiles()를 사용할 수 있습니다. 저렇게 Buffer를 통해 파일을 업로드 할 수도 있고

```ts
await fileUploaderInput.setInputFiles(path.join(__dirname, 'myfile.pdf'));
```

위처럼 경로에 실제 파일을 올려두고 테스트 하는 방법이 있습니다.

### 4. CLI로 테스트 실행하기

Playwright은 GUI를 통해 테스트를 실행하는 방식을 제공하지만, 컴퓨터의 사양으로 인해 테스트가 느리게 동작하거나 워커가 테스트의 숫자를 감당하지 못해 GUI 상에서 테스트가 실패하는 케이스가 더러 있습니다.

그럴때는 CLI를 통해 테스트를 실행해 볼 수 있습니다.

```
// 전체 테스트 실행
npx playwright test

//list test 파일의 테스트만 실행
npx playwright test list-test.spec.ts
```

<img src="https://github.com/YeongseoYoon/yeongseo-blog/assets/86523545/0c188789-d8b5-4ffc-a904-ee6096b9bb88" />
테스트를 실행 후 위와 같은 내용을 볼 수 있습니다. 이때 아래와 같은 커맨드를 실행해보겠습니다.

```
// 리포트 보기
npx playwright show-report
```

<img src="https://github.com/YeongseoYoon/yeongseo-blog/assets/86523545/921ad13a-30d9-49f1-bfc3-0d4878c03845" />

해당 테스트의 리포트를 볼 수 있습니다.

Playwright에서는 리포트들을 저장해 둘 수 있는 기능도 존재하는데,
사실 CI에서 문제가 되었을 경우에는 PR을 올릴 수 없게 되고 배포 자체가 진행되지 않기 때문에 리소스만 잡아먹고 크게 필요하다고 판단하지 않아 저희 회사에서는 사용하고 있지 않습니다.

### 5. UI로 테스트 실행하기

다음으로는 아래와 같은 커맨드를 실행해보겠습니다.

```
npx playwright test list-test --headed
```

<img src="https://github.com/YeongseoYoon/yeongseo-blog/assets/86523545/905c85c4-f5ea-4ff7-837b-bc2cf339e7df" />

그럼 위 사진과 같이 브라우저와 매우 유사한 창을 보게 됩니다. 이 창 내부에서 작성한 테스트의 실제 동작을 확인할 수 있습니다.
테스트 실패가 날 경우에도 어떤 곳에서 실패가 나는지 빠르게 확인 가능해 유용합니다.

```
npx playwright test --ui
```

이번에는 GUI를 통해 테스트를 실행해보겠습니다. 위 커맨드를 입력하면 다음과 같은 창이 보여집니다.

<img src="https://github.com/YeongseoYoon/yeongseo-blog/assets/86523545/26d05155-ce6d-4f73-b891-3d3af4610263" />

전체 파일을 테스트할 수도, 하나의 파일을 테스트할 수도 있습니다. 하나의 파일에 있는 각각의 테스트들도 버튼을 통해 수행 가능합니다.

<img src="https://github.com/YeongseoYoon/yeongseo-blog/assets/86523545/adc51d28-12db-4bad-b08a-fdfdf423124d" />

실행을 하고 만약 오류가 나면, 어떤 코드상에서 어떤 이유로 오류가 났는지 보여집니다. 이때 오류가 난 화면도 스냅샷처럼 보여지기때문에, 언제쯤 어떤 이유로 오류가 났는지 유추할 수 있습니다.

<img src="https://github.com/YeongseoYoon/yeongseo-blog/assets/86523545/2aed87d5-4e8b-4934-93ad-709906ef0446" />

다른 테스팅 툴은 모르겠지만, Playwright GUI의 장점은 개발자 도구를 켜볼 수 있다는 것입니다.

<img src="https://github.com/YeongseoYoon/yeongseo-blog/assets/86523545/faa8bb2f-3553-4e6b-b80e-4c2d25a84849" />

만약 오류가 난 시점이 있을 경우, 해당 시점을 클릭하고 우측 상단의 버튼을 누르면 새 창으로 스냅샷 화면을 볼 수 있습니다.

<img src="https://github.com/YeongseoYoon/yeongseo-blog/assets/86523545/5ab99408-99b6-46a7-a80c-9a2d47492d60" />
이처럼 스냅샷에서도 개발자 도구를 통해 요소를 확인할 수 있어 조금 더 편리하게 테스트 코드 작성과 수정이
가능합니다.

### 6. Codegen으로 내가 코드 작성안해도 알아서 일시키기

처음 테스트 코드 구성을 어떻게 해야할지 감이 오지 않을때, 해볼만한 방법이 있습니다.
저는 현재 data e2e 속성을 부여해 사용하고 있어 잘 사용하지 않지만 테스트 코드를 처음 작성할 때는 유용하게 사용했던 방법입니다.

```
npx playwright codegen
```

위 커맨드를 입력하고 뜨는 창에서 테스트를 원하는 사이트로 들어갑니다. 그 이후 실 사용자의 행동처럼 동작하면 코드가 기록됩니다.

<img src="https://github.com/YeongseoYoon/yeongseo-blog/assets/86523545/47b5d744-bd74-4cdf-a60c-120ff2f72bcb" />

Playwright을 사용하면서 제가 유용하게 사용했던 작은 팁들을 공유했습니다. 테스트 코드로 인해 고통받는 누군가에게 도움이 되길 바라며 글 마칩니다.

### ✏️ 출처

https://playwright.dev/docs <br/>
