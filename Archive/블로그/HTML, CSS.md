## 가상요소
- 선택자로 선택한 요소의 뒤에 붙여 표기하는 미리 약속된 키워드를 말합니다.
```css
/* 사용 방법 */
선택할 요소 ::before { ... }
선택할 요소 ::after { ... }
선택할 요소 ::not (제외시킬 요소) { ... }
/* 예시 */
p::before { 
	content: attr(data-before-text);
	margin-right: 0.625rem; 
}

```

- content 속성에 표시하는 속성 값은 선택자로 선택한 요소의 속성 값을 가져올 수도 있습니다

[선택자 Docs](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements)
## 가상 클래스
- HTML 요소의 특정 상태나 행동을 선택하기 위한 CSS 선택자입니다.
- 가장 많이 사용하는 클래스 종류 
  - :hover    : 마우스를 롤오버 했을 때
  - :active    : 요소를 클릭했을 때
  - :forcus    : 요소가 포커스 될 때 (입력 태그 등)
  - :visited   : 방문한 적이 있는 링크
```css
/* 예시 */
a:hover { 
	color: red; 
}
```

## (번외) 특성 선택자 []
- 주어진 특성의 존재 여부나, 그 값에 따라 요소 선택
[참고 링크](https://developer.mozilla.org/ko/docs/Web/CSS/Attribute_selectors)


[공식 문서](https://developer.mozilla.org/en-US/docs/Web/CSS)
[참고 블로그](https://coding-factory.tistory.com/898)