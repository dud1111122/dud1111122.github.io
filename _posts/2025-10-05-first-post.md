---
layout: post
title: How to post
date: 2025-10-05
last_modified_at: 2025-10-05
tags: []
toc: true
author: CHoYoungJoo
---

## 1\. 포스트 메타데이터: 프론트 매터(Front Matter) 사용법

가장 상단에 `---`로 감싸진 영역을 **프론트 매터**라고 부릅니다. 여기에 포스트의 모든 정보를 설정할 수 있으며, 이 정보가 Jekyll 테마에 의해 처리되어 웹페이지에 반영됩니다.

| 속성 (Attribute) | 용도 및 기능 | 작성 예시 |
| :--- | :--- | :--- |
| `layout` | 이 포스트에 사용할 레이아웃 파일(HTML 템플릿)을 지정합니다. (예: `_layouts/post.html`) | `layout: post` |
| `title` | 포스트의 제목입니다. 브라우저 탭, 페이지 제목, 검색 결과 등에 표시됩니다. | `title: Welcome to Not Pure Poole` |
| `date` | 포스트가 처음 작성된 날짜와 시간입니다. 시간대(Timezone) 정보도 포함됩니다. | `date: 2020-09-29 23:18 +0800` |
| `last_modified_at` | 포스트가 마지막으로 수정된 날짜입니다. 이 날짜를 기준으로 정렬하거나 '최근 수정됨' 정보를 표시할 수 있습니다. | `last_modified_at: 2020-10-01 01:08:25 +0800` |
| `tags` | 포스트를 분류하는 데 사용되는 태그 목록입니다. 검색 기능이나 태그 클라우드 생성에 유용합니다. **(핵심 활용 요소)** | `tags: [jekyll theme, jekyll, tutorial]` |
| `toc` | **TOC (Table of Contents)**, 즉 목차의 활성화 여부를 결정합니다. | `toc: true` (목차 활성화) |
| `author` | 이 포스트를 작성한 작성자를 표현할 수 있습니다. | `author: CHoYoungJoo` |

-----

## 2\. 본문 마크다운 및 HTML 요소 활용법

프론트 매터 다음부터는 마크다운 구문을 사용하여 본문을 작성합니다.

### A. 텍스트 강조 및 인라인 스타일

| 요소 | 목적 | 마크다운/HTML 문법 | 예시 결과 |
| :--- | :--- | :--- | :--- |
| **굵게** | 중요한 단어 또는 구문 강조 | `**To bold text**` 또는 `<strong>To bold text</strong>` | **To bold text** |
| *이탤릭* | 기울임꼴로 강조 | `*To italicize text*` 또는 `<em>To italicize text</em>` | *To italicize text* |
| 하이라이트 | 특정 부분을 표시 | `<mark>To highlight</mark>` | <mark>To highlight</mark> |
| **링크** | 외부 또는 내부 페이지 연결 | `<a href="URL">표시 텍스트</a>` | [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/HTML/Element) |
| 인용 블록 | 긴 인용문이나 중요 메시지 표시 | `> Curabitur blandit tempus porttitor.` | > Curabitur blandit tempus porttitor. |
| 약어 | 용어의 전체 의미를 툴팁으로 표시 | `<abbr title="풀네임">약어</abbr>` | <abbr title="HyperText Markup Langage">HTML</abbr> |
| 취소선/삽입 | 삭제되거나 삽입된 텍스트 표시 | `<del>Deleted</del>` / `<ins>inserted</ins>` | <del>Deleted</del> / <ins>inserted</ins> |
| 캡션 박스 | 특정 메시지나 주의 사항을 박스로 표시 | `{: .message }` | Welcome to **Not Pure Poole**! This is an example post to show the layout. 바로 다음 줄에 사용되어 스타일 적용. |

### B. 코드 블록 및 목차 요소

  * **제목/헤딩 (목차 자동 생성)**

      * `# Heading` (가장 큰 제목. 보통 포스트 제목으로 대체됨)
      * `## Heading` (대제목. 목차에 포함됨)
      * `### Sub Heading` (중제목. 목차에 포함됨)

  * **인라인 코드**: 문장 중간에 짧은 코드를 표시할 때 사용합니다.

      * `Inline code is available with the \`<code>\` element.`

  * **코드 블록 (Syntax Highlighting)**

      * `{% highlight javascript %}` ... `{% endhighlight %}` Liquid 태그를 사용하거나, 마크다운의 펜스(Triple backticks \`)를 사용합니다.
      * **코드 블록 옵션**: `js` 다음에 \*\*`linenos`\*\*를 추가하면 줄 번호가 표시됩니다.
        
        {% highlight js linenos %}
        ```html
        // 여기에 코드 내용
        var example = "Fixing the syntax error";
        console.log(example);
        {% endhighlight %}
        ``` dd

### C. 목록 및 정의 목록

  * **순서 없는 목록 (Unordered List)**: `-` 또는 `*`를 사용합니다.
    ```markdown
    - Praesent commodo cursus magna
    - Donec id elit non mi porta gravida
    ```
  * **순서 있는 목록 (Ordered List)**: 숫자를 사용합니다.
    ```markdown
    1. Vestibulum id ligula porta felis
    2. Cum sociis natoque penatibus
    ```
  * **정의 목록 (Definition List)**: 용어와 설명을 나열합니다. (HTML 태그 사용)
    ```html
    <dl>
      <dt>용어</dt>
      <dd>설명</dd>
    </dl>
    ```

### D. 각주 (Footnotes)

각주 기능을 사용하면 본문 하단에 참고 문헌이나 보충 설명을 깔끔하게 넣을 수 있습니다.

1.  **본문에 각주 위치 지정**: `[^fn-고유ID]` 형식으로 작성합니다.
      * 예시: `Clicking this number[^fn-sample_footnote]`
2.  **포스트 하단에 각주 내용 정의**: 본문 어디에 정의하든 Jekyll이 자동으로 포스트 맨 아래에 모아서 표시합니다.
      * 예시: `[^fn-sample_footnote]: Handy! Now click the return link to go back.`

### E. 이미지 삽입 및 정렬

  * **기본 이미지 삽입**: 마크다운 기본 문법을 사용합니다.
      * `![설명 텍스트](이미지 URL "툴팁 텍스트")`
  * **이미지 중앙 정렬**: 이미지 마크다운 뒤에 `{:`와 `}`를 사용하여 CSS 클래스를 적용합니다.
      * `![placeholder](http://placehold.it/400x200 "Medium example image"){: .align-center}`

### F. 테이블 (Tables)

| 요소 | 용도 | 마크다운/HTML 문법 |
| :--- | :--- | :--- |
| **헤더/바닥글** | 테이블의 제목(`<thead>`)과 합계(`<tfoot>`) 표시 | HTML `<table>`, `<thead>`, `<tfoot>` 태그를 사용해야 함. |
| **본문** | 실제 데이터 행을 표시 | HTML `<tbody>`, `<tr>`, `<td>` 태그를 사용해야 함. (일반 마크다운 테이블도 가능하나, 이 예시에서는 HTML을 사용함) |

-----