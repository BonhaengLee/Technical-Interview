# 효율적인 CSS를 작성하는데 있어서 어려움은 무엇인가요? #

먼저, 브라우저는 selector가 `맨 오른쪽(key selector)부터 왼쪽으로 일치하는지 확인`합니다.  

브라우저는 selector에 따라 DOM의 요소를 필터링하고 해당 부모요소가 일치하는지 식별합니다.  

selector 체인의 길이가 짧을수록 브라우저는 해당 요소가 selector와 **일치하는지 여부를 빠르게 판별**할 수 있습니다. 따라서 **태그 selector와 보편적인 selector 사용을 피해야** 합니다.  
이들은 많은 요소가 매치되기 때문에 부모가 일치하는지 여부를 판단하기 위해 브라우저가 많은 작업을 해야합니다.

BEM (Block Element Modifier) 방법론에서는 `모두 단일 클래스`를 갖고, **계층구조가 필요한 곳에서는 클래스의 이름을 확장**하기를 권장합니다.  
따라서 selector를 쉽고 효율적으로 재정의할 수 있습니다.

`어떤 CSS 속성이 reflow, repaint, compositing을 트리거하는지` 알아두고, 가능하면 `레이아웃(reflow 유발)를 변경하는 스타일은 피해야` 합니다.  