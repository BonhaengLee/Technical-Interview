# JavaScript 템플릿을 사용한 적이 있나요? 사용해봤다면, 어떤 라이브러리를 사용했나요? #

네, Handlebars, JSX를 사용해봤습니다.
JSX가 JavaScript에 가깝고 배워야 할 새로운 문법이 거의 없어서 좋아합니다.  
요즘에는, Third-party 라이브러리에 의존하지 않고 템플릿을 만드는 빠른 방법으로 ES2015 템플릿 문자열 리터럴을 사용할 수도 있습니다.

```javasript
const template = `<div>My name is: ${name}</div>`;
```

그러나 템플릿 라이브러리와 달리 컨텐츠가 이스케이프되지 않아 잠재적 XSS 공격을 알고 있어야 합니다.  

## 이스케이프 처리 ##

HTML 문자를 이스케이프(escape) 처리하면 `스크립트나 HTML 태그의 기능은 제거되지만 입력한 내용은 그대로 브라우저에서 확인`할 수 있다. 예를 들어 태그의 시작을 의미하는 **< 문자를 이스케이프 처리하면 &lt;라는 문자로 바뀐다.**

<https://wikidocs.net/127508>

## XSS 방어 기법 ##

데이터를 입력할 때, DB에 insert할 때, select할 때, 출력할 때 모두 필터를 거치게 하여 XSS 공격을 방어할 수 있습니다.  

간단히 생각해서 `데이터를 이스케이프하여 모든 태그를 막으면 원천적으로 봉쇄할 수 있지만, 이 경우는 모든 HTML 태그를 막아버리기 때문에, 대부분의 사이트에서 처럼 스타일을 먹여야 하는 경우에는 적용할 수 없습니다.`  

그렇기 때문에 기본적으로 모든 태그를 막고, 사이트에 필요한 `일부 태그만 허용하는 방식으로 필터를 제작`할 수 있습니다.  

또는 OWASP Antisamy나 NAVER Lucy XSS Filter와 같은 신뢰할 수 있는 `기존 라이브러리`를 사용하는 것도 좋은 방법입니다.  

<https://medium.com/humanscape-tech/xss%EC%99%80-csrf-fe0e219b4c38>
