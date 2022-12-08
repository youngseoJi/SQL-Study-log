설치와 접속하는데.. 고생을 많이했기에 간단하게 공유합니당!
(스터디분께서 알려주셨어요!)


# SQL설치방법 
## 터미널 다운
1. Homebrew를 이용해 xSQL을 설치한다.
> **brew install mysql**



- 혹시 Homebrew가 다운이 안되어있다면 터미널(iterm2)에 아래 코드를 작성하시면 다운로드 할 수 있습니다.
> $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
  [Homebrew 사이트](https://brew.sh/index_ko)



2. 비밀번호 설정한다.  따옴표 안에 비밀번호만 작성해주면된다. 
>**ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '비밀번호';**

아래코드가 비밀번호 만들기 성공!![](https://images.velog.io/images/estell/post/b1c031ae-524c-4283-9d0f-f5b46fb219e7/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-01-22%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%2012.35.55.png)**주의! 비밀번호를 대문자 소문자 특수문자 포함 8문자 이상으로 작성해야 나중에 오류가 안뜬다! (엄청해맨부분)**

3. MYSQL 데이터베이스에 아래 코드를 통해 접속한다.
 mysql에 접속한다. password열쇠모양 -> 위에서 만든 비밀번호 치고 Enter을 치면 접속된다. 
>**mysql -u root -p**  
**Enter**
![](https://images.velog.io/images/estell/post/3878c07d-1a52-4a23-be62-f9f23151397e/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-03-04%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%201.43.01.png)
(접속할 데이터베이스  u : 접속할 계정설정 -P: 비밀번호 설정 옵션)

4. **use문:** 사용할 데이터 베이스를 지정하는 형식 
>**use mysql**
mysql 이라닌 데이터 베이스를 사용할 것이다 (데이터베이스 있을경우, 생성했을 경우)


# mySQL UI 다운
[mySQL UI](https://www.youtube.com/watch?v=8r1W_7nuo2U&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=3)
저는 터미널에서 기본적인 설정을 한 후에 UI만 다운받고 사용하는 거라, 터미널에서 안했을 시에는 위에 링크로 다운부터 설정까지 해주세요!

1. 아래 링크로 들어가서 다운로드를 누르고, macOS 버전 다운로드한다.
>https://www.mysql.com/products/workbench/

![](https://images.velog.io/images/estell/post/ccbf8b71-870a-4af2-ae3d-14d426671075/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-01-22%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%2012.41.00.png)
![](https://images.velog.io/images/estell/post/8be3ae20-4675-4271-a6f1-c7ec4eea95f3/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-01-22%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%2012.41.13.png)
3. 로그인 하지말고, no thanks 링크를 누른다! -> 파일이 다운받아진다.
![](https://images.velog.io/images/estell/post/0c74e211-c7d7-4c39-bd36-b1b144b96233/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-01-22%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%2012.41.34.png)
![](https://images.velog.io/images/estell/post/7cc3c70e-79ed-4733-9162-7c37576a1709/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-01-22%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%2012.44.21.png)
3. Launchpad에 다운받아진 mySQL UI을 누르면, 메인페이지 connenxtions에 있는 (이미 터미널에서 만든) root계정을 누르고 비번을 치면 접속완료!
![](https://images.velog.io/images/estell/post/08d3bdc0-0572-400a-85b7-e78fd99c4ec4/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202022-01-22%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%201.21.05.png)
