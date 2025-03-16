---
title: '효과적인 React Query 키 관리 전략'
date: '2025-03-16T13:33:27.982Z'
summary: '만능열쇠 키'
tags: ['TANSTACKQUERY']
---

TanStack Query는 서버 상태 관리를 위한 강력한 라이브러리로 널리 사용되고 있습니다. 
그러나 프로젝트 규모가 커질수록 쿼리 키 관리는 점점 복잡해지고, 잘못된 관리 방식은 유지보수 문제를 일으킬 수 있습니다. 


이 글에서는 제가 프로젝트에서 마주한 쿼리 키 관리 문제와 이를 개선하기 위한 전략을 공유하고자 합니다.

# 기존 쿼리 키 관리의 문제점

저희 회사의 프로젝트에서는 다음과 같이 쿼리 키를 관리하고 있었습니다.

```tsx
// src/shared/policy.ts 쿼리키 선언
export const QUERY_KEYS = {   
   강의: (id: number) => ['강의', id], 
   // ... 다른 수많은 쿼리 키들
}

// src/shared/hooks/use강의.ts 쿼리 선언
export const use강의 = (id: number) => {
  return useQuery(QUERY_KEYS.강의(id), () => get강의(id));
};
```
이 방식에는 다음과 같은 문제점이 있었습니다.

1. 쿼리 키와 쿼리 로직의 분리: 쿼리 키는 policy.ts 파일에, 실제 쿼리 로직은 훅 파일에 있어 연관된 코드가 분산되어 있었습니다.
2. 타입 안전성 부족: 쿼리 무효화(invalidation) 시 타입 추론이 되지 않아 휴먼 에러가 발생할 가능성이 높았습니다.

```tsx
// 오타 발생 가능성이 높음
await queryClient.invalidateQueries({ queryKey: ['강의'] }); //여기서 '강이'라고 한다면?
```
3. 구조화되지 않은 키: 1depth 키 구조와 하드코딩된 문자열은 확장성과 일관성을 저해했습니다.
4. 유지보수의 어려움: 한 policy파일의 한 `QUERY_KEYS` 객체에 각각의 feature에 대한 쿼리키가 혼재되어있어 관련 키들이 도메인별로 그룹화되지 않아 관리가 어려웠습니다.
5. 컨벤션이 따로 없음: 쿼리키 관리 컨벤션이 따로 없어 팀 내에서 모두가 동일한 컨벤션을 따르지 않아 쿼리키 관리에 어려움이 있었습니다. 
특히 쿼리 무효화를 해주는 경우엔 어떤 동료는 쿼리키를 하드 코딩 된 문자열로 무효화하고, 어떤 동료는 쿼리키 배열의 0번째 인덱스를 통해 무효화 하는 등 컨벤션의 모호함이 있었습니다.


# 개선 방안
이러한 문제를 해결하기 위해 다음 세 가지 방안을 검토했습니다.

## 1. 직접 쿼리 키 선언 방식
```tsx
export const 강의Queries = {
  all: ['강의'] as const,
  목록Key: () => [...강의Queries.all, '목록'] as const,
  목록Query: (filters: 강의필터) => ({
    queryKey: [...강의Queries.목록Key(), filters],
    queryFn: () => 강의목록가져오기(filters)
  }),
}
```
    
### 장점:
- 추가적인 라이브러리 의존성이 없음
- 프로젝트 특성에 맞게 자유롭게 커스터마이징 가능

### 단점:
- 타입 안전성이 낮아 추가 코드 필요
- 키 구조 확장 시 일관성 유지 어려움

## 2. QueryKeyFactory 라이브러리 도입
```tsx
import { createQueryKeyStore } from '@lukemorales/query-key-factory';

const 강의Queries = createQueryKeyStore('강의', {
  all: null,
  목록Key: () => ({
    queryKey: ['목록'],
  }),
  목록Query: (filters: 강의필터) => ({
    queryKey: ['목록', filters], 
    queryFn: () => 강의목록가져오기(filters)
  }),
});
```

### 장점:
- 보일러플레이트 감소
- 뛰어난 타입 안전성
- 일관된 구조 강제 가능

### 단점:
- 추가 의존성 발생
- 커스터마이징 제한

## 3. Query Option API 활용 (TanStack Query v5)
```tsx
const 강의Queries = {
  all: ['강의'] as const,
  목록Key: () => [...강의Queries.all, '목록'] as const,
  목록Query: (filters: 강의필터) =>
    queryOptions({
      queryKey: [...강의Queries.목록Key(), filters],
      queryFn: () => 강의목록가져오기(filters),
    }),
};
```

### 장점:
- 보일러플레이트 감소
- 뛰어난 타입 안전성
- 외부 라이브러리 의존도 감소

### 단점:
- v4에서 v5로의 마이그레이션 필요

# 선택: Query Option API를 활용한 Factory 패턴
여러 옵션을 검토한 결과, Query Option API를 활용한 Factory 패턴이 장기적으로 가장 유지보수하기 좋은 방식이라고 판단했습니다. 
해당 방식은 다음과 같은 이점을 가져갈 수 있다고 판단하였습니다.

## 1. 쿼리 키와 쿼리 함수의 동일 위치 배치
- 관련 코드를 함께 배치해 코드 응집도 향상
- React Query 메인테이너인 TkDodo가 권장하는 방식


## 2. 타입 안전성
- 자동 완성 지원
- 쿼리 무효화 시 타입 오류 사전 방지

## 3. 구조화된 키
- 도메인별 계층적 키 구조로 일관성 유지
- 쿼리 간 관계가 명확하게 표현됨

## 4. 확장성
- 새로운 쿼리 추가 시 기존 구조에 쉽게 통합

# 구현 세부사항
## 파일 구조
쿼리와 쿼리 키를 가깝게 배치하기 위해 다음과 같은 폴더 구조를 채택했습니다.

```ts
hooks/
  ├── 강의/
  │   ├── index.ts       # 관련 훅 정의
  │   └── queries.ts     # 쿼리 팩토리 정의
  ├── 멤버/
  │   ├── index.ts
  │   └── queries.ts
  └── ...
```
각 도메인 폴더는 다음 두 파일을 포함합니다.

- `index.ts`: 해당 도메인과 관련된 React Query 훅들을 정의하고 내보냅니다.
- `queries.ts`: 해당 도메인의 쿼리 키와 쿼리 로직을 구조화하여 정의합니다.


## 쿼리 컨벤션
효과적인 쿼리 키 관리와 일관성 있는 코드 작성을 위해 다음과 같은 컨벤션을 정립했습니다.

### 1. 네이밍 규칙
- 쿼리 객체: 도메인명 뒤에 Queries 접미사 추가
```ts
// 예: 강의Queries
export const 강의Queries = { ... };
```

- 기본 쿼리 키: 관련 키 뒤에 Key 접미사 추가
```ts
// 예: 목록Key, 상세Key
목록Key: () => [...강의Queries.all, '목록'] as const,
```

- 쿼리 함수: 관련 함수 뒤에 Query 접미사 추가
```ts
// 예: 목록Query, 상세Query
목록Query: (필터: 강의필터) => queryOptions({ ... }),
```


### 2. 계층 구조
- 최상위 키: 모든 쿼리 객체는 all 속성으로 시작
```ts
all: ['강의'] as const,
```

- 중간 계층 키: 파라미터 없이 정의하여 그룹 무효화 용이하게 함
```ts
// 파라미터 없이 정의
목록Key: () => [...강의Queries.all, '목록'] as const,
```

- 최하위 쿼리: 파라미터를 받아 최종 쿼리 정의
```ts
// 파라미터를 포함한 최종 쿼리
목록Query: (필터: 강의필터) =>
  queryOptions({
    queryKey: [...강의Queries.목록Key(), 필터],
    queryFn: () => 강의목록가져오기(필터),
  }),
```


### 3. queryOptions 사용

- 모든 쿼리 정의에 queryOptions 사용
- 쿼리 키는 배열 스프레드 연산자로 기본 키 확장


## Factory화 된 쿼리 사용 예시

```ts
export const 강의Queries = {
  // 1. 최상위 키 (all)
  all: ['강의'] as const,
  
  // 2. 기본 쿼리 키 (Key 접미사)
  목록Key: () => [...강의Queries.all] as const,
  
  // 3. 쿼리 함수 (Query 접미사)
  목록Query: (필터: 강의필터) =>
    queryOptions({
      queryKey: [...강의Queries.목록Key(), 필터],
      queryFn: () => 강의목록가져오기(필터),
    }),
};
```

### 1. 모든 관련 쿼리 무효화시 다음과 같이 사용할 수 있습니다.
```ts
export const use강의등록 = () => {
  const queryClient = useQueryClient();

  const { mutateAsync: 강의등록, isPending } = useMutation({
    mutationFn: (강의Ids: number[]) => 강의등록Api(강의Ids),
    onSuccess: () => {
      queryClient.invalidateQueries({
        queryKey: 강의Queries.all, // all로 작성
      });
    },
  });

  return { 강의등록, isPending };
};
```

### 2. 도메인과 관련된 모든 쿼리를 무효화해야 할 때는 다음처럼 base queryKey를 사용할 수 있습니다.
```ts
 queryClient.invalidateQueries({queryKey: 강의Queries.강의목록Key()});
 
 ---
 
  강의목록Key: () => [...강의Queries.all, '목록'] as const, //여기엔 파라미터 넘기지 않음
  강의목록Query: ({
    상품id,
    강의id,
    offset,
    limit,
  }: {
    상품id: number;
    강의id: number;
    offset?: number;
    limit?: number;
  }) =>
    queryOptions({
      queryKey: [...강의Queries.강의목록Key(), 상품id, 강의id, offset, limit],
      queryFn: () =>
        get강의목록(상품id, 강의id, offset, limit).then(({ data }) => ({
          data: data.data,
          meta: data.meta,
        })),
    }),
 
```
base queryKey인 강의목록Key()는 파라미터를 받지 않도록 구성하여, 강의 도메인 아래의 모든 강의 관련 쿼리를 한 번에 무효화할 수 있습니다. 
만약 강의목록Key()가 파라미터를 받는다면 특정 파라미터에 해당하는 쿼리만 무효화되기 때문에 base queryKey에는 파라미터를 넘기지 않습니다.


### 3. 더 좁은 범위로 관련된 쿼리의 무효화만 필요하면 다음과 같이 사용할 수 있습니다.
```ts
 queryClient.invalidateQueries({ queryKey: 강의Queries.강의목록Query(필터).queryKey });
```

현재 이 글을 작성하는 시점에서는 저희 프로젝트 중 하나의 서비스에 대한 마이그레이션이 완료되었습니다. 
다른 서비스들의 경우 새로 작성하는 기능들부터 이 패턴을 적용하는 점진적 접근법을 취하고 있습니다.

아직 초기단계기 때문에 다른 팀원들이 새로운 컨벤션에 적응하는 데 약간의 학습 곡선이 있었지만, 명확한 가이드라인과 코드 리뷰를 통해 빠르게 패턴이 정착되었습니다. 
특히 컨벤션이 없고 명확하지 않았던 기존 코드에서는 쿼리 무효화를 할 때 어떻게 작성해야할지를 고민하는 비용이 발생했던 것에 비해 현재는 그러한 비용이 훨씬 줄었다고 생각합니다.

만약 저희 팀처럼 쿼리 키를 어떻게 하면 효과적으로 관리할지에 대해 고민하시는 분들이 계시다면 이 글이 도움이 되었으면 좋겠습니다.


### ✏️ 출처
- [Query Options](https://tanstack.com/query/latest/docs/framework/react/guides/query-options)
- [Query Key Factory Library](https://tanstack.com/query/latest/docs/framework/react/community/community-projects#query-key-factory)
- [Effective Query Key](https://tkdodo.eu/blog/effective-react-query-keys)