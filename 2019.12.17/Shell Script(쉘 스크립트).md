# Shell Script(쉘 스크립트)

### 쉘

사용자가 입력한 명령을 해석해서 커널에게 전달하거나, 커널의 처리 결과를 사용자에게 전달하는 역할을 한다.



## 우분투의 Bash Shell

* #### 우분투의 셸은 Bash(bourne Again Shell)

* #### Bourne Sheel을 기반으로 Korn Shell과 C Shell의 좋은점을 합한 것

  * 쉘의 기능

    * Alias 기능(명령 단축 기능)

    * History기능

    * 연산 기능

    * Job Control 기능

    * 자동 이름 완성 기능

    * 프롬프트 제어 기능

    * 명령 편집 기능

      
      

* #### 환경 변수

  Shell은 여러가지 환경 변수 값을 갖는데, 설정된 환경 변수는 echo $환경변수이름 형식으로 명령 실행 가능하다.

  | 환경변수 | 설명                      | 환경변수     | 설명                          |
  | -------- | ------------------------- | ------------ | ----------------------------- |
  | HOME     | 현재 사용자의 홈 디렉터리 | PATH         | 실행 파일 찾는 디렉터리       |
  | LANG     | 기본 지원 언어            | PWD          | 사용자 현재 작업 디렉터리     |
  | TERM     | 로그인 터미널 타입        | SHELL        | 로그인해서 사용하는 쉘        |
  | USER     | 현재 사용자 이름          | DISPLAY      | X 디스플레이 이름             |
  | COLUMNS  | 현재 터미널의 컬럼 수     | LINES        | 터미널 라인 수                |
  | PS1      | 1차 명령 프롬프트 변수    | PS2          | 2차 명령 프로므트 변수        |
  | BASH     | bash쉘 경로               | BASH_VERSION | bash 버전                     |
  | HISTFILE | 히스토리 파일 경로        | HISTSIZE     | 히스토리 파일에 저장되는 개수 |
  | HOSTNAME | 호스트 이름               | USERNAME     | 현재 사용자 이름              |
  | LOGNAME  | 로그인 이름               | LS_COLORS    | ls 명령어의 화장자 색상 옵션  |
  | MAIL     | 메일 보관 경로            | OSTYPE       | 운영체제 타입                 |

  

1. ##### 변수 선언

   * 변수는 미리 선언하지 않음

   * 변수에 넣는 모든 값음 문자열로 취급한다.

   * 변수는 대소문자 구분

   * 변수 대입시에 = 좌우에 공백 없어야함.

     ```shell
     #!/bin/sh
     variable=1234
     Variable2="Yes Yes"
     Variable2=7+5
     ```

2. ##### 입력, 출력

   * $라는 문자가 들어간 글자를 출력하려면 ''로 묶거나 앞에 \를 붙여야한다. 변수는 " "로 묶거나 묶지 않아도 됨.

   * 입력에서 공백이 입력될 수 있다면 "$변수" 형식으로 받아들이는게 안전하다.

     ```shell
     #var1.sh
     #!/bin/sh
     myvar="Hi Kim"
     echo $myvar
     echo "$myvar"
     echo '$myvar'
     echo \$myvar
     echo "Input Value :"  
     echo '$myvar' = $myvar
     exit 0
     ```

3. ##### 숫자 계산

   * 변수에 값이 들어가며 모두 문자열로 취급되기에 수식을 쓰기 위해서는 expr 키워드를 사용해야한다 expr은 ``로 묶어줘야한다. 

   * 수식에 괄호를 이용하거나 곱하기(*)를 사용할때는 앞에 역슬래시를 반드시 붙여줘야 한다.

     ```shell
     #numcal.sh
     #!/bin/sh
     num1=100
     num2=$num1+200
     echo $num2
     num3=`expr $num1 + 200`
     echo $num3
     num4=`expr  \(  $num1   +   200 \)  /   10  \* 2`
     echo $num4
     exit 0;
     ```

4. ##### Parameter

   * 파라미터는 $1 $2등의 형태를 갖고 0부터 시작한다. 

   * apt-get install openssh-server 이라면 띄어쓰기를 기준으로 $0 $1 $2가 된다.

     ```shell
     #paravar.sh
     #!/bin/sh
     echo "Excuted File name is $0"
     echo "First Parameter is $1"
     echo "Entire Parameter is $2"
     ```

5. ##### if문

   * [ 조건 ] 의 문자 사이사이에는 반드시 공백이 있어야한다.

     ```shell
     #if2.sh
     #!/bin/sh
     if [ "woo" != "woo" ]
     then
         echo "It is TRUE"
     else
         echo "It is FALSE"
     fi
     
     if [ 100 -eq 200 ]
     then
         echo "100 And 200 is Equal Value"
     else
         echo "100 And 200 is NOT Equal Value"
     fi
     exit 0
     ```

     

     

     * 비교 연산자

       * 문자열

       | 비교방법               | 결과                       |
       | ---------------------- | -------------------------- |
       | "문자열1" = "문자열2"  | 두 문자열이 같으면 참      |
       | "문자열1" != "문자열2" | 두 문자열이 같지 않으면 참 |
       | -n "문자열"            | 문자열이 NULL이 아니면 참  |
       | -z "문자열"            | 문자열이 NULL이면 참       |

       * 산술 비교

       | 산술 비교       | 결과                           |
       | --------------- | ------------------------------ |
       | 수식1 -eq 수식2 | 두 수식(변수)이 같으면 참      |
       | 수식1 -ne 수식2 | 두 수식(변수)이 같지 않으면 참 |
       | 수식1 -gt 수식2 | 수식1이 크다면 참              |
       | 수식1 -ge 수식2 | 수식1이 크거나 같으면 참       |
       | 수식1 -lt 수식2 | 수식1이 작으면 참              |
       | 수식1 -le 수식2 | 수식1이 작거나 같으면 참       |
       | !수식           | 수식이 거짓이라면 참           |

   

6. ##### 파일과 관련된 조건

   ​		

   | 파일 조건   | 결과                              |
   | ----------- | --------------------------------- |
   | -d 파일이름 | 파일이 디렉터리라면 참            |
   | -e 파일이름 | 파일이 존재하면 참                |
   | -f 파일이름 | 파일이 일반 파일이면 참           |
   | -g 파일이름 | 파일에 set-group-id가 설정되면 참 |
   | -r 파일이름 | 파일 읽기가 가능하면 참           |
   | -s 파일이름 | 파일 크기가 0이 아니면 참         |
   | -u 파일이름 | 파일에 set-suer-id가 설정되면 참  |
   | -w 파일이름 | 파일이 쓰기 가능 상태이면 참      |
   | -x 파일이름 | 파일이 실행가능 상태이면 참       |

   ```shell
   #if4.sh
   #!/bin/sh
   fname=/lib.systemd/system/cron.service
   if [ -f $fname ]
   then
       head -5 $fname
   else
       echo "Cron Server is NOT installed"
   fi
   exit 0
   ```

   

7. ##### case~esac문

   다중 분기문 C언어의 case문과 동일

   ```shell
   #case1.sh
   #!/bin/sh
   
   case "$1" in
       start)
           echo "Start ~~~";;
       stop)
           echo "Stop ~~!!";;
       restart)
           echo "Restart !!";;
       *)
           echo "I Don't know What is it";;
   esac
   exit 0
   ```

   

   ```shell
   #case2.sh
   #!/bin/sh
   echo "Is Linux funny? (Yes/No)"
   read answer
   case $answer in yes | y | Y | Yesy | YES)		## |로 구분해놓은 것 중에 하나면 됨
       echo "Good"
       echo "Study Hard! ^^";;
   [nN]*)											##앞에 n이나 N이 들어가는 모든 단어 인정
       echo "Bad :(";;
       *)											##지정값 이외의 것들
       echo "You Must Input Yes or No"
       exit 1;;
   esac
   exit 0
   ```

   

8. ##### AND, OR 관계 연산자

   * and는 -a 또는 &&를 사용

   * or는 -o 또는 ||를 사용

   * -a와 -o는 괄호등의 특수 문자 앞에서는 \를 붙여써야 한다.

     ```shell
     #andor.sh
     #!/bin/sh
     echo "Input filename What you want to see"
     read fname
     if [ -f $fname ] && [ -s $fname ] ; then
         head -5 $fname
     else
         echo "File is NOT Exist or FileSize is 0"
     fi
     exit 0
     
     ```

     
     

9. ##### 반복문

   ```shell
   #forin1.sh
   #!/bin/sh
   hap=0
   for i in 1 2 3 4 5 6 7 8 9 10
   do
       gap = `expr $sum + $i`
   done
   echo "Sumation 1 ~ 10 :" $sum
   exit 0
   ##############################################
   #forin2.sh
   #!/bin/sh
   for fname in $(ls *.sh)
   do
       echo "--------$fname------"
       head -3 $fname
   done
   exit 0
   ##############################################
   #while1.sh
   #!/bin/sh
   while [ 1 ]			#조건문 조건에 1이 들어가면 TRUE
   do
       echo "Ubuntu 16.04 LTS"
   done
   exit 0
   ##############################################
   #while2.sh
   #!/bin/sh
   sum=0
   i=1
   while [ $1 -le 10 ]
   do 
       hap=`expr   $sum + $i`
       i=`expr $i + 1`
   done
   echo "sumation 1~10 :"$sum
   exit 0
   ##############################################
   #while3.sh
   #!/bin/sh
   
   echo "Enter password"
   read passwd
   
   while [ $passwd != "1234" ] #참인동안
   do
       echo "Incorrect reEnter the password"
       read passwd
   done
   echo "Passed!~~"
   exit 0
   ##############################################
   ```

   

10. ##### until문

    ```shell
    untill [ $1 -gt 10 ]        #거짓인동안
    do 
        hap=`expr   $sum + $i`
        i=`expr $i + 1`
    done
    echo "sumation 1~10 :"$sum
    exit 0
    
    ```

    

11. ##### break, continue,exit,return 

    ```shell
    #bce.sh
    #!/bin/sh
    echo "Start Infinite Input (b):break, c(continue), e(exit)"
    while [ 1 ] : do
        read Input
        case $input in b | B)
            break;;
        c | C)
            echo "if you excute conitnue, move to while condition"
            continue;;
        e | E)
            echo "if you excute exit, this Terminates the Program"
            exit 1;;
        esac;
    done
    echo "if you excute break, you can see this comment"
    exit 0
    ```

    * 함수, 프로그램, 반복문을 종료할 때 씀.

      

12. ##### 사용자 정의 함수

    ```shell
    #userDefineFunc.sh
    #!/bin/sh
    MyFunction()
    {
        echo "This Echo From Function"
    }
    
    echo "Program Started"
    MyFunction
    echo "Program Terminated"
    exit 0
    ########################################################
    #functionWithParam
    #!/bin/sh
    sumation()
    {
        echo `expr $1 + $2`
    }
    
    echo "add 20 to 10 "
    sumation 10 20
    exit 0
    ########################################################
    ```

    

13. ##### eval

    * 문자열을 명령문으로 인식하고 실행시킨다.

      ```shell
      #eval.sh
      #!/bin/sh
      str="ls -l eval.sh"
      echo $str
      eval $str
      exit 0
      ```

      
      

14. ##### export

    * 외부 변수로 선언, 선언한 변수를 다른 프로그램에서도 사용할 수 있게 한다.

      ```shell
      #export.sh
      #!/bin/sh
      
      #exp1.sh
      echo $var1
      echo $var2
      exit 0
      
      #exp2.sh
      var1="Local Variable"
      export var2="Global Variable"
      ```

      

15. #####  printf

    * C언어의 printf 함수와 비슷하게 형식을 지정해서 출력

      ```shell
      #printf.sh
      #!/bin/sh
      var1=100.5
      var2="Funniest Linux ~~"
      printf( "%5.2f \n\n \t %s \n" %var1  "$var2")
      exit
      ```

      

16. ##### set과 $(명령)

    * 리눅스 명령을 결과로 사용하려면 이용한다. 결과를 파라미터로 사용하고 싶을때는 set명령어와 함께 사용한다


      ```shell
      #set.sh
      #!/bin/sh
      echo "Today's Date is $(date)"
      set $(date)
      echo "todya is $4"
      exit 0
      ```

    

17. ##### Shift

    * Parameter 변수를 왼쪽으로 한 단계씩 아래로 쉬프트 (이동) 시킨다.

      ```shell
      #set.sh
      #!/bin/sh
      echo "Today's Date is $(date)"
      set $(date)
      echo "todya is $4"
      exit 0
      
      #shift.sh
      #!/bin/sh
      Myfunc()
      {
          str=""
          while [ "$1" != " " ] ; 
          do
              str="$str $1"
              shift
          done
          echo $str
      }
      Myfunc AAA BBB CCC DDD EEE FFF GGG HHH III JJJ KKK
      exit 0
      ```

      







