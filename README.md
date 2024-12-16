 첫 HTML 연습


4.10

GFM은 테이블을 가능하게합니다

테이블은 단일 머리글 행, 머리글과 데이터를 구분하는 구분자 행, 0 개 이상의 데이터 행으로 구성된 행과 열이있는 데이터의 배열입니다.

각 행은 파이프 (|)로 구분 된 인라인이 구문 분석되는 임의의 텍스트를 포함하는 셀로 구성됩니다. 읽기의 명확성과 파싱 모호성이있는 경우 선행 및 후행 파이프도 권장됩니다. 파이프와 셀 내용 사이의 공간이 잘립니다. 블록 수준 요소는 테이블에 삽입 할 수 없습니다.

구분자 행은 내용이 하이픈 (-) 뿐인 셀과 선택적으로 각각 왼쪽, 오른쪽 또는 가운데 정렬을 나타내는 선행 또는 후행 콜론 (:) 또는 둘 다로 구성됩니다.

예 198
```
| foo | bar |
| --- | --- |
| baz | bim |
```

| foo | bar |
| --- | --- |
| baz | bim |

한 열의 셀이 길이와 일치 할 필요는 없지만 일치하는 경우 읽기가 더 쉽습니다. 마찬가지로 선행 및 후행 파이프를 사용하면 일관성이 없을 수 있습니다.

예제 199
```
| abc | defghi |
:-: | -----------:
bar | baz
```

| abc | defghi |
:-: | -----------:
bar | baz

다른 인라인 범위 내부를 포함하여 이스케이프 처리하여 셀 콘텐츠에 파이프를 포함합니다.

예제 200
```
| f\|oo  |
| ------ |
| b `\|` az |
| b **\|** im |
```

| f\|oo  |
| ------ |
| b `\|` az |
| b **\|** im |

테이블은 첫 번째 빈 줄 또는 다른 블록 수준 구조의 시작에서 나뉩니다.

예제 201
```
| abc | def |
| --- | --- |
| bar | baz |
> bar
```

| abc | def |
| --- | --- |
| bar | baz |
> bar

예 202
```
| abc | def |
| --- | --- |
| bar | baz |
bar

bar
```

| abc | def |
| --- | --- |
| bar | baz |
bar

bar

헤더 행 은 셀 수의 구분 기호 행 과 일치해야합니다 . 그렇지 않으면 테이블이 인식되지 않습니다.

예제 203
```
| abc | def |
| --- |
| bar |
 ```
 
| abc | def |
| --- |
| bar |

테이블 행의 나머지 부분은 셀 수에 따라 다를 수 있습니다. 헤더 행의 셀 수보다 적은 수의 셀이있는 경우 빈 셀이 삽입됩니다. 더 큰 경우 초과는 무시됩니다.

예 204
```
| abc | def |
| --- | --- |
| bar |
| bar | baz | boo |
 ```

| abc | def |
| --- | --- |
| bar |
| bar | baz | boo |

본문에 행이 없으면 <tbody>HTML 출력에 no 가 생성됩니다.

예 205
```
| abc | def |
| --- | --- |
```

| abc | def |
| --- | --- |

5.3Task list items (extension)

GFM은 목록 항목에 대해 추가 처리 단계가 수행되는 작업 목록 확장을 활성화합니다.

작업 목록 항목은 첫 번째 블록이 작업 목록 항목 마커로 시작하는 단락이고 다른 콘텐츠 앞에 하나 이상의 공백 문자가있는 목록 항목입니다.

작업 목록 항목 마커는 선택적인 수의 공백, 왼쪽 대괄호 ([), 공백 문자 또는 소문자 또는 대문자의 문자 x, 그리고 오른쪽 대괄호 (])로 구성됩니다.

렌더링되면 작업 목록 항목 마커가 의미 확인란 요소로 바뀝니다. HTML 출력에서 ​​이것은 <input type = "checkbox"> 요소입니다.

대괄호 사이의 문자가 공백 문자이면 확인란이 선택 취소됩니다. 그렇지 않으면 확인란이 선택됩니다.

이 사양은 체크 박스 요소가 상호 작용하는 방법을 정의하지 않습니다. 실제로 구현자는 체크 박스를 비활성화되거나 변경 불가능한 요소로 자유롭게 렌더링 할 수 있으며, 최종 렌더링 된 문서에서 동적 상호 작용 (즉, 확인, 선택 해제)을 동적으로 처리 할 수 ​​있습니다.


Example 279
```
- [ ] foo
- [x] bar
```

- [ ] foo
- [x] bar

작업 목록은 임의로 중첩 될 수 있습니다.

Example 280
```
- [x] foo
  - [ ] bar
  - [x] baz
- [ ] bim
```

- [x] foo
  - [ ] bar
  - [x] baz
- [ ] bim

6.5 Strikethrough (extension)

GFM은 추가 강조 유형을 사용할 수있는 취소 선 확장을 활성화합니다.

취소 선 텍스트는 두 개의 물결표 (~)로 둘러싸인 텍스트입니다.

Example 491
```
~~hi~~ Hello, world!
```

~~hi~~ Hello, world!

일반 강조 구분 기호와 마찬가지로 새 단락은 취소 선 구문 분석을 중단합니다.

Example 492
```
This ~~has a

new paragraph~~.
```

This ~~has a

new paragraph~~.


6.9 Autolinks (extension)

GFM은 자동 링크 확장을 활성화하여 더 많은 조건에서 자동 링크를 인식합니다.

자동 링크는 더 작은 환경에서 인식되지만 <및 to>를 사용하지 않고도 구성 할 수 있습니다. 이러한 인식 된 모든 자동 링크는 행 시작, 공백 뒤 또는 구분 문자 *, _, ~ 및 (.

확장 된 www 자동 링크는 텍스트 www. 뒤에 유효한 도메인이 있습니다. 유효한 도메인은 마침표 (.)로 구분 된 영숫자, 밑줄 (_) 및 하이픈 (-) 세그먼트로 구성됩니다. 마침표가 하나 이상 있어야하며 도메인의 마지막 두 세그먼트에는 밑줄이 없어야합니다.

shceme http가 자동으로 삽입됩니다.


Example 621
```
<www.commonmark.org>
```

<www.commonmark.org>

유효한 도메인 뒤에 0 개 이상의 공백이 아닌 <문자가 올 수 있습니다.

Example 622
```
Visit www.commonmark.org/help for more information.
```

Visit www.commonmark.org/help for more information.

그런 다음 확장 된 자동 링크 경로 유효성 검사를 다음과 같이 적용합니다.

후행 구두법 (특히?,!,., ,, :, *, _ 및 ~)은 링크 내부에 포함될 수 있지만 자동 링크의 일부로 간주되지 않습니다.

Example 623
```
Visit www.commonmark.org.

Visit www.commonmark.org/a.b.
```

Visit www.commonmark.org.

Visit www.commonmark.org/a.b.

자동 링크가 종료되면) 전체 자동 링크에서 괄호 총 수를 검색합니다. 여는 괄호보다 닫히는 괄호 수가 더 많은 경우, 괄호 안에 자동 링크를 포함하기 위해 자동 링크의 일치하지 않는 후행 괄호 부분은 고려하지 않습니다.

Example 624
```
www.google.com/search?q=Markup+(business)

www.google.com/search?q=Markup+(business)))

(www.google.com/search?q=Markup+(business))

(www.google.com/search?q=Markup+(business)
```

www.google.com/search?q=Markup+(business)

www.google.com/search?q=Markup+(business)))

(www.google.com/search?q=Markup+(business))

(www.google.com/search?q=Markup+(business)

이 검사는 링크가 닫히는 괄호로 끝날 때만 수행되므로, 자동 링크 내부에 괄호만 있는 경우 다음과 같은 특별한 규칙이 적용되지 않습니다.

Example 625
```
www.google.com/search?q=(business))+ok
```

www.google.com/search?q=(business))+ok

자동 링크가 세미콜론(;)으로 끝나는 경우 엔티티 참조와 유사한지, 이전 텍스트가 하나 이상의 영숫자 뒤에 있는지 확인합니다. 그렇다면 자동 링크에서 제외됩니다.

Example 626
```
www.google.com/search?q=commonmark&hl=en

www.google.com/search?q=commonmark&hl;
```

www.google.com/search?q=commonmark&hl=en

www.google.com/search?q=commonmark&hl;

< 자동 링크를 즉시 종료합니다

Example 627
```
www.commonmark.org/he<lp
```

www.commonmark.org/he<lp


확장 URL 자동 링크는 확장 자동 링크 경로 검증에 따라 스키마 중 하나가 http:// 또는 https:// 뒤에 유효한 도메인이 있는 다음 공백이 아닌 0개 이상의 문자를 사용할 때 인식됩니다.

Example 628
```
http://commonmark.org

(Visit https://encrypted.google.com/search?q=Markup+(business))
```

http://commonmark.org

(Visit https://encrypted.google.com/search?q=Markup+(business))


텍스트 노드 내에서 이메일 주소가 인식되면 확장된 이메일 자동 링크가 인식됩니다. 이메일 주소는 다음 규칙에 따라 인식됩니다.

-영숫자 또는 ., -, _ 또는 +인 하나 이상의 문자입니다.
-@ 기호입니다.
-영숫자 또는 - 또는 _, 마침표(.)로 구분된 하나 이상의 문자입니다. 적어도 하나의 기간이 있어야 합니다. 마지막 문자는 - 또는 _ 중 하나일 수 없습니다.
-스키마 메일 수신자:가 생성된 링크에 자동으로 추가됩니다.

Example 629
```
foo@bar.baz
```

foo@bar.baz

+는 @ 앞에 발생할 수 있지만, 그 후에 발생할 수는 없습니다.

Example 630
```
hello@mail+xyz.example isn't valid, but hello+xyz@mail.example is.
```

hello@mail+xyz.example isn't valid, but hello+xyz@mail.example is.

., - 및 _는 @의 양쪽에서 발생할 수 있지만, .만 전자 메일 주소 끝에 발생할 수 있습니다. 이 경우에는 주소의 일부로 간주되지 않습니다.

Example 631
```
a.b-c_d@a.b

a.b-c_d@a.b.

a.b-c_d@a.b-

a.b-c_d@a.b_
```

a.b-c_d@a.b

a.b-c_d@a.b.

a.b-c_d@a.b-

a.b-c_d@a.b_


6.11 Disallowed Raw HTML (extension)

GFM은 HTML 출력을 렌더링 할 때 다음 HTML 태그가 필터링되는 tagfilter 확장을 활성화합니다.

<제목>
<텍스트 영역>
<스타일>
<xmp>
<iframe>
<noembed>
<프레임 없음>
<스크립트>
<일반 텍스트>
필터링은 선행 <을 엔티티 & lt;로 대체하여 수행됩니다. 이러한 태그는 특히 HTML이 고유 한 방식으로 해석되는 방식을 변경하기 때문에 선택되며 (즉, 중첩 된 HTML은 다르게 해석 됨) 일반적으로 다른 렌더링 된 마크 다운 콘텐츠의 맥락에서 바람직하지 않습니다.

다른 모든 HTML 태그는 그대로 유지됩니다.

Example 653
```
<strong> <title> <style> <em>

<blockquote>
  <xmp> is disallowed.  <XMP> is also disallowed.
</blockquote>
 ```
 
 <strong> <title> <style> <em>

<blockquote>
  <xmp> is disallowed.  <XMP> is also disallowed.
</blockquote>
