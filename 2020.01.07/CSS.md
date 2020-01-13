# CSS

Cascade Style Sheet의 약자로 출력 스타일을 지원하는 것



### CSS의 기본형식

```
선택자{스타일속성1:값; 스타일속성2:값;}
```



* ##### 스타일 시트의 내부 선언

  ```html
  <head>
      <style>
          body{background:skyblue;}
          h3{background:blue;color:white; text-align:center;}
      </style>
  </head>
  ```

  

* ##### 스타일시트의 외부 선언

  * style01.css

    ```css
    body{background:skyblue;}
    h3{background:blue;color:white; text-align:center;}
    ```

  * html

    ```html
    <head>
        <link rel="stylesheet" type="text/css" href="style01.css">
    </head>
    ```

  

* ##### @import 문을 이용한 외부 선언

  * style01.css

    ```css
    body{background:skyblue;}
    h3{background:blue;color:white; text-align:center;}
    ```

  * html

    ```html
    <head>
        <style> @import url("style01.css"); </style>
    </head>
    ```

    또는

    ```html
    <head>
        <style> @import "style01.css"; </style>
    </head>
    ```

    

* ##### CSS3 스타일 시트의 인라인 선언

  ```html
  <h3 style="background:gold; text-align:center;">
      HTML5!
  </h3><hr>
  <ul>
      <li>HTML5</li>
      <li style="color:red;">CSS3</li>
  </ul>
  ```

  

  

* CSS 스타일 오버로딩

  * mystyle.css

    ```css
    h1, h2, h4{background: orange;}
    ```

  * html

    ```html
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>Insert title here</title>
    	<style> h1,h2,h5,pre{background:skyblue;}</style>
    	<style> @import "mystyle.css";</style>
    	<style> h1,div {bakground:blue;color:white;}</style>
    </head>
    
    <body>
    	<h1>HTML5웹프로그래밍1(h1)</h1>
    	<h1 style="background:black;">HTML5 웹 프로그래밍2(h1)</h1>
    	<h2>HTML5 웹 프로그래밍3(h2)</h2>
    	<div><h3>HTML5웹 프로그래밍4(h3)</h3> </div>
    	<pre><h3>HTML5 웹프로그래밍5(h3)</h3> </pre>
    	<h3>HTML5 웹 프로그래밍6(h5)</h3>
    	<h4>HTML5 웹 프로그래밍7(h4)</h4>
    </body>
    </html>
    ```

    

  

### CSS3 선택자

* 태그 선택자

  ```html
  <style>
      h3{background:skyblue;}
      li{color:blue;}
  </style>
  ```

  

* 아이디 선택자

  ```html
  <style>
      #s1{background:skyblue;}
      li#s2{color:red;}
  </style>
  
  <h3>HTML5</h3><hr>
  <ul>
      <li>HTML5</li>
      <li id="s1"> CSS3 </li>
      <li>javascript</li>
      <li id="s2"> HTML API</li>
  </ul>
  ```

  

* 클래스 선택자

  ```html
  <style>
      .c1{background:skyblue;}
      .c2{color:blue;}
      .c3{color:red;}
      #a1{background:orange;}
  </style>
  
  <h3>HTML5</h3><hr>
  <ol>
      <li class="c1 c3">HTML</li>
      <ul>
          <li class="c2">HyperLink</li>
          <li class="c2">입력양식</li>
      </ul>
      <li>CSS3</li>
      <ul>
          <li class="c3">선택자</li>
          <li class="c3">CSS 스타일 속성</li>
          <li id="a1">레이아웃</li>
      </ul>
      <li class="c1 c2">javascript</li>
  </ol>
  ```

  

















