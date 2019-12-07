# Markdown Guide

* ### Headings

  * 문법

  ```markdown
  # Heading Level1
  ## Heading Level2
  ### Heading Level3
  #### Heading Level4
  ##### Heading Level5
  ###### Heading Level6
  ```

  

  * 결과

  # Heading Level1

  ## Heading Level2
  ### Heading Level3
  #### Heading Level4
  ##### Heading Level5
  ###### Heading Level6





* ### Alternate Syntax

  * 문법

    ```markdown
    Heading level 1
    ===============
    
    Heading level 2
    ---------------
    ```

  

  * 결과

  Heading level 1
  ===============

  Heading level 2
  ---------------





* ### Paragraphs

  * 문법

    ```markdown
    I really like using Markdown.
    
    I think I'll use it to format all of my documents from now on.
    ```

    

  * 결과

    I really like using Markdown.

    I think I'll use it to format all of my documents from now on.



* ### Line Breaks

  * 문법

    ```markdown
    This is the first line.  
    And this is the second line.
    ```

  

  *  결과

    This is the first line.  
    And this is the second line.

    

* ### Bold

  * 문법

    ```markdown
    I just love **bold text**.
    I just love __bold text__.
    Love**is**bold
    ```

    

  * 결과

    I just love **bold text**.
    I just love __bold text__.
    Love**is**bold

  

* ### Italic

  * 문법

    ```markdown
    Italicized text is the *cat's meow*.
    Italicized text is the _cat's meow_.
    A*cat*meow
    ```

    

  * 결과

    Italicized text is the *cat's meow*.
    Italicized text is the _cat's meow_.
    A*cat*meow

  

* ### Bold and Italic

  * 문법

    ```markdown
    This text is ***really important***.
    This text is ___really important___.
    This text is __*really important*__.
    This text is **_really important_**.
    ```

    

  * 결과

    This text is ***really important***.
    This text is ___really important___.
    This text is __*really important*__.
    This text is **_really important_**.

  

* ### Blockquotes

  * 문법

    ```markdown
    > Dorothy followed her through many of the beautiful rooms in her castle.
    ```

    

  * 결과

    > Dorothy followed her through many of the beautiful rooms in her castle.



* ### Blockquotes with Multiple Paragraphs

  * 문법

    ```markdown
    > Dorothy followed her through many of the beautiful rooms in her castle.
    >
    > The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
    ```

    

  * 결과

    > Dorothy followed her through many of the beautiful rooms in her castle.
    >
    > The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.



* ### Nested Blockquotes

  * 문법

    ```markdown
    > Dorothy followed her through many of the beautiful rooms in her castle.
    >
    >> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.
    ```

    

  * 결과

    > Dorothy followed her through many of the beautiful rooms in her castle.
    >
    > > The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.

    

* ### Blockquotes with Other Elements

  * 문법

    ```markdown
    > #### The quarterly results look great!
    >
    > - Revenue was off the chart.
    > - Profits were higher than ever.
    >
    >  *Everything* is going according to **plan**.
    ```

    

  * 결과

    > #### The quarterly results look great!
    >
    > - Revenue was off the chart.
    > - Profits were higher than ever.
    >
    >  *Everything* is going according to **plan**.

  

* ### Lists

  * 문법

    ```markdown
    1. First item
    2. Second item
    3. Third item
    4. Fourth item
    
    1. First item
    1. Second item
    1. Third item
    1. Fourth item
    
    1. First item
    8. Second item
    3. Third item
    5. Fourth item
    
    1. First item
    2. Second item
    3. Third item
        1. Indented item
        2. Indented item
    4. Fourth item
    ```

    

  * 결과

    1. First item
    2. Second item
    3. Third item
    4. Fourth item

    

    1. First item
    1. Second item
    1. Third item
    1. Fourth item

    

    1. First item
    8. Second item
    3. Third item
    5. Fourth item

    

    1. First item
    2. Second item
    3. Third item
        1. Indented item
        2. Indented item
    4. Fourth item

    

    

* ### Unordered Lists

  * 문법

    ```markdown
    - First item
    - Second item
    - Third item
    - Fourth item
    
    * First item
    * Second item
    * Third item
    * Fourth item
    
    + First item
    * Second item
    - Third item
    + Fourth item
    
    - First item
    - Second item
    - Third item
        - Indented item
        - Indented item
    - Fourth item
    ```

    

  * 결과

    - First item
    - Second item
    - Third item
    - Fourth item

    

    * First item
    * Second item
    * Third item
    * Fourth item

    

    + First item
    * Second item
    - Third item

    + Fourth item

    

    - First item
    - Second item
    - Third item
        - Indented item
        - Indented item
    - Fourth item

    

* ### Paragraphs

  * 문법

    ```markdown
    *   This is the first list item.
    *   Here's the second list item.
    
        I need to add another paragraph below the second list item.
    
    *   And here's the third list item.
    ```

    

  * 결과

    *   This is the first list item.
    *   Here's the second list item.

        I need to add another paragraph below the second list item.

    *   And here's the third list item.



* ### Blockquotes

  * 문법

    ```markdown
    *   This is the first list item.
    *   Here's the second list item.
    
        > A blockquote would look great below the second list item.
    
    *   And here's the third list item.
    ```

    

  * 결과

    *   This is the first list item.
    *   Here's the second list item.

        > A blockquote would look great below the second list item.

    *   And here's the third list item.

  

* #### Code Blocks

  * 문법

    ```markdown
    1.  Open the file.
    2.  Find the following code block on line 21:
    
            <html>
              <head>
                <title>Test</title>
              </head>
    
    3.  Update the title to match the name of your website.
    ```

    

  * 결과

    1.  Open the file.
    2.  Find the following code block on line 21:

            <html>
              <head>
                <title>Test</title>
              </head>

    3.  Update the title to match the name of your website.

    

* ### Images

  * 문법

    ```markdown
    1.  Open the file containing the Linux mascot.
    2. Marvel at its beauty.
    
       ![tux](./image/tux.png?raw=true)
       ![tux](./image/tux.png?raw=true "Linux mascot")
       [![tux](./image/tux.png?raw=true "Linux mascot")](https://www.linux.com/)
    
    3. Close the file.
    ```

    

  * 결과

    1. Open the file containing the Linux mascot.

    2. Marvel at its beauty.

       ![tux](./Image/tux.png?raw=true)

       ![tux](./Image/tux.png?raw=true"Linux mascot")

       [![tux](./Image/tux.png?raw=true"Linux mascot")](https://www.linux.com/)

    3.  Close the file.

    

  

* ### Escaping Backticks

  * 문법

    ```markdown
    At the command prompt, type `nano`.
    ```

    

  * 결과

    At the command prompt, type `nano`.

    

* ### Escaping Backticks

  * 문법

    ```markdown
        <html>
          <head>
          </head>
        </html>
    ```

    

  * 결과

        <html>
          <head>
          </head>
        </html>
    

* ### Horizontal Rules

  * 문법

    ```markdown
    ***
    
    ---
    
    _________________
    ```

    

  * 결과

    ***

    ---

    _________________

    

* ### Links

  * 문법

    ```markdown
    My Github is [Github.com/kiheyunkim](https://github.com/kiheyunkim).
    ```

    

  * 결과

    My Github is [Github.com/kiheyunkim](https://github.com/kiheyunkim).

    

* ### Adding Titles

  * 문법

    ```markdown
    My Github is [Github.com/kiheyunkim](https://github.com/kiheyunkim "My Github").
    ```

    

  * 결과

    My Github is [Github.com/kiheyunkim](https://github.com/kiheyunkim "My Github").

    

    

* ### URLs and Email Addresses

  * 문법

    ```markdown
    <https://www.markdownguide.org>
    <fake@example.com>
    ```

    

  * 결과

    <https://www.markdownguide.org>
    <fake@example.com>

  

* ### Formatting Links

  * 문법

    ```markdown
    I love supporting the **[EFF](https://eff.org)**.
    This is the *[Markdown Guide](https://www.markdownguide.org)*.
    See the section on [`image`](image).
    ```

    

  * 결과

    I love supporting the **[EFF](https://eff.org)**.
    This is the *[Markdown Guide](https://www.markdownguide.org)*.
    See the section on [`image`](image).

    

* ### Escaping Characters

  * 문법

    ```markdown
    \* Without the backslash, this would be a bullet in an unordered list.
    ```

    

  * 결과

    \* Without the backslash, this would be a bullet in an unordered list.

  

  * 같이 사용할 수 있는 것들
    \ ` * _ {} [] () # + - . ! |

  

  

  

  

  

  

  
  

  

  
  
















































