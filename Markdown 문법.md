## 1. 헤더 (Headers)

- 6가지의 제목을 나타내는 문법이 있는데 `#`을 사용 (글머리는 1 ~ 6까지만 지원)

```python
# 제목 1
## 제목 2
### 제목 3
#### 제목 4
##### 제목 5
###### 제목 6
####### 제목 7 (지원 않됨)
```

# [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#%EC%A0%9C%EB%AA%A9-1)제목 1

## [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#%EC%A0%9C%EB%AA%A9-2)제목 2

### [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#%EC%A0%9C%EB%AA%A9-3)제목 3

#### [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#%EC%A0%9C%EB%AA%A9-4)제목 4

##### [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#%EC%A0%9C%EB%AA%A9-5)제목 5

###### [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#%EC%A0%9C%EB%AA%A9-6)제목 6

####### 제목 7 (지원 않됨)

---

## [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#2-%EC%A4%84%EB%B0%94%EA%BF%88-line-breaks)2. 줄바꿈 (Line Breaks)

- `<br>` 태그를 이용해서 줄바꿈을 사용할 수 있는데, 간단하게 **띄어쓰기 두 번**을 하고 enter을 누르면 줄을 바꿀 수 있음

```python
첫번째 문장입니다. <br>
두번째 문장입니다.  
세번째 문장입니다.  
네번째 문장입니다.
```

첫번째 문장입니다.  
두번째 문장입니다.  
세번째 문장입니다.  
네번째 문장입니다.

---

## [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#3-%EB%AA%A9%EB%A1%9D-list)3. 목록 (List)

### [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#3-1-%EC%88%9C%EC%84%9C%EA%B0%80-%EC%9E%88%EB%8A%94-%EB%AA%A9%EB%A1%9D%EB%B2%88%ED%98%B8)3-1) 순서가 있는 목록(번호)

- 순서가 있는 목록은 숫자와 점을 사용

```python
1. 첫번째
2. 두번째
3. 세번째
```

1. 첫번째
2. 두번째
3. 세번째

### [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#3-2-%EC%88%9C%EC%84%9C%EA%B0%80-%EC%97%86%EB%8A%94-%EB%AA%A9%EB%A1%9D)3-2) 순서가 없는 목록

- 순서가 없는 목록은 글머리 기호( *, +, - ) 를 사용

```python
+ 첫번째
+ 두번째
+ 세번째

- 첫번째
- 두번째
- 세번째

* 첫번째
* 두번째
* 세번째
```

```python
+ 첫번째
    + 두번째
        + 세번째
        
* 1단계
  - 2단계
    + 3단계
      + 4단계
```

- 첫번째
    - 두번째
        - 세번째

- 1단계
    - 2단계
        - 3단계
            - 4단계

---

## [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#4-%EC%9D%B8%EC%9A%A9%EB%AC%B8-blockquote)4. 인용문 (BlockQuote)

- `>`을 사용하여 블럭인용문자를 삽입 할 수 있음

```python
> 첫번째 인용구입니다.
>> 두번째 인용구입니다.
>>> 세번째 인용구입니다.
```

> 첫번째 인용구입니다.
> 
> > 두번째 인용구입니다.
> > 
> > > 세번째 인용구입니다.

---

## [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#5-%EC%BD%94%EB%93%9Ccode%EB%B8%94%EB%9F%AD)5. 코드(Code)블럭

## 5-1) "```" 을 이용

- 코드블럭코드("```") 시작점에 사용하는 언어를 선언하여 문법강조(Syntax highlighting)이 가능

````

```python
def print_text():
    print("Hello Wolrd!!")
```
````

```python
def print_text():
    print("Hello Wolrd!!")
```

---

## [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#6-%EC%88%98%ED%8F%89%EC%84%A0-horizontal-rule)6. 수평선 (Horizontal Rule)

- 각 기호를 3개 이상 입력
- 마크다운 문서를 미리보기로 출력할 때 페이지 나누기 용도로 많이 사용

```python
* * *

***

*****

- - -

---------------------------------------
```

## [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#7-%EA%B0%95%EC%A1%B0-emphasis)7. 강조 (Emphasis)

```python
*기울어진 글씨*
_기울어진 글씨_
**굵은 글씨**
__굵은 글씨__
~~취소선 글씨~~
```

_기울어진 글씨_ _기울어진 글씨_ **굵은 글씨** **굵은 글씨** ~~취소선 글씨~~

---

## [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#8-%EB%A7%81%ED%81%AC-links)8. 링크 (Links)

[](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#8-1-%EC%B0%B8%EC%A1%B0%EB%A7%81%ED%81%AC)

8-1) 참조링크

```python
[link keyword][id]
[id]: URL "Optional Title here"
```

Link: [Google](https://google.com/ "Go google")

### [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#8-2-%EC%9E%90%EB%8F%99%EC%97%B0%EA%B2%B0)8-2) 자동연결

일반적인 URL 혹은 이메일주소인 경우 적절한 형식으로 링크를 형성

```
* 외부링크: <http://example.com/>
* 이메일링크: <address@example.com>
```

- 외부링크 : [http://example.com/](http://example.com/)
- E-mail Link : [address@example.com](mailto:address@example.com)

---

## [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#9-%EC%9D%B4%EB%AF%B8%EC%A7%80-image)9. 이미지 (Image)

```python
![Markdown Image](asset/images/test_image.jpg "Tooltip Message")
```

[![Markdown Image](https://user-images.githubusercontent.com/69428232/144952302-a7333133-4320-4079-9fdc-8382d18c136f.jpg "Tooltip Message")](https://user-images.githubusercontent.com/69428232/144952302-a7333133-4320-4079-9fdc-8382d18c136f.jpg)

이미지의 크기나 정렬은 html 문법을 이용  
`<img width="" height=""></img>`를 이용하며, 정렬을 위해서는 추가적으로 `<div align="center"> </div>`  을 이용  
width, height에 직접 사이즈를 지정하거나 비율(%)로 지정 할 수 있음

```python
<img src="asset/images/test_image.jpg" width="450px" height="300px" title="px(픽셀) 크기 설정" alt="Markdown Image"></img><br/>
<div align="center">
  <img src="asset/images/test_image.jpg" width="20%">
</div>
```

[![Markdown Image](https://user-images.githubusercontent.com/69428232/144952302-a7333133-4320-4079-9fdc-8382d18c136f.jpg "px(픽셀) 크기 설정")](https://user-images.githubusercontent.com/69428232/144952302-a7333133-4320-4079-9fdc-8382d18c136f.jpg)  

[![](https://user-images.githubusercontent.com/69428232/144952302-a7333133-4320-4079-9fdc-8382d18c136f.jpg)](https://user-images.githubusercontent.com/69428232/144952302-a7333133-4320-4079-9fdc-8382d18c136f.jpg)

---

## [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#10-%ED%91%9C-table)10. 표 (Table)

### [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#10-1-%EC%9D%BC%EB%B0%98%EC%A0%81%EC%9D%B8-%ED%91%9C)10-1) 일반적인 표

- 테이블 안에 `|` 파이프 기호를 사용하려면 파이프 기호 대신에 `&#124;` 를 입력

```python
|제목|&#124;내용&#124;|설명|
|------|---|---|
|테스트1|테스트2|테스트3|
|테스트1|테스트2|테스트3|
|테스트1|테스트2|테스트3|
```

|제목|\|내용\||설명|
|---|---|---|
|테스트1|테스트2|테스트3|
|테스트1|테스트2|테스트3|
|테스트1|테스트2|테스트3|

### [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#10-2-%EC%85%80-%EC%A0%95%EB%A0%AC)10-2) 셀 정렬

- `:` 문자로 정렬을 정의

```python
|제목|내용|설명|
|:---|---:|:---:|
|왼쪽정렬|오른쪽정렬|중앙정렬|
|왼쪽정렬|오른쪽정렬|중앙정렬|
|왼쪽정렬|오른쪽정렬|중앙정렬|
```

| 제목   |    내용 |  설명  |
| :--- | ----: | :--: |
| 왼쪽정렬 | 오른쪽정렬 | 중앙정렬 |
| 왼쪽정렬 | 오른쪽정렬 | 중앙정렬 |
| 왼쪽정렬 | 오른쪽정렬 | 중앙정렬 |

### [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#10-3-%EC%85%80-%ED%99%95%EC%9E%A5)10-3) 셀 확장

- 사이가 비어있으면 자동으로 확장

```python
|제목|내용|설명|
|:---|:---:|---:|
||중앙에서확장||
|||오른쪽에서 확장|
|왼쪽에서확장||
```

|제목|내용|설명|
|:--|:-:|--:|
||중앙에서확장||
|||오른쪽에서 확장|
|왼쪽에서확장|||

### [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#10-4-%EC%85%80-%EA%B0%95%EC%A1%B0)10-4) 셀 강조

- 일반적인 text와 마찬가지로 `*` 와 `**` 를 통해 이탤릭/강조를 표시할 수 있습니다. `span tag`를 사용하면 컬러도 표시 가능

```python
|제목|내용|설명|
|---|---|---|
|테스트1|*강조1*|테스트3|
|테스트1|**강조2**|테스트3|
|테스트1|<span style="color:red">강조3</span>|테스트3|
```

|제목|내용|설명|
|---|---|---|
|테스트1|_강조1_|테스트3|
|테스트1|**강조2**|테스트3|
|테스트1|강조3|테스트3|

---

## [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#11-%EA%B0%81%EC%A3%BC-footnote)11. 각주 (Footnote)

```python
각주<sup>[1](#각주 이름)</sup>

<a name="각주 이름">1</a>: 각주에 대한 설명
```

각주[1](#각주 이름)

1: 각주에 대한 설명

---

## [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#12-%EC%A0%91%EA%B8%B0-fold)12. 접기 (Fold)

```python
<details><summary>Click Me</summary>
Good!!
</details>    
```

Click Me

---

## [](https://gist.github.com/yunwoong7/83246af10e1831233a870c26104e4a1f#13-%EC%9D%B4%EC%8A%A4%EC%BC%80%EC%9D%B4%ED%94%84-backslash-escapes)13. 이스케이프 (Backslash Escapes)

- 마크다운으로 글을 작성하다 보면 `*` 문자나 `_` 문자 등을 사용하고 싶은 경우 `\` 문자로 회피

```python
강조는 \* 문자 혹은 \_ 문자를 사용
```

강조는 * 문자 혹은 _ 문자를 사용