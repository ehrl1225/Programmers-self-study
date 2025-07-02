[[Javascript]]에 타입을 넣은 언어로 타임의 차이로 인한 오류를 방지하고자 만들어낸 것이다.
유지 보수성을 높여준다.
하지만 Javascript로 변환과정을 거친다.

# type

type을 지정할 수 있다.
```typescript
export type PostDto = {
	id: number;
	title: string;
};
```
이 방식으로 작성이 가능하고

```typescript
import type {PostDto} from "@/type/post"
```
이 방식으로 불러올 수 있다.

## 중복된 코드 없애기

### 뺴기
```typescript
export type PostWithContentDto = {
	id: number;
	title: string;
	content: string;
}

export type PostDto = Omit<PostWithContentDto, "title"|"content">;
```

### 더하기
```typescript
export type PostDto = {
	id: number;
	title: string;
}

export type PostDtoWithContent =  "content" & PostDto
```

# interface
type과 같이 사용가능한데 상속도 가능하다.
그래서 중복된 코드를 줄일 수 있다.

