---
""
---
| ||C:\Users\kiyun>mkdir git<br>C:\Users\kiyun>cd git<br>C:\Users\kiyun\git>git clone https://github.com/ita-bility/ita-bility.github.io<br>'git'은(는) 내부 또는 외부 명령, 실행할 수 있는 프로그램, 또는 배치 파일이 아닙니다.|`

git이 무슨 의미인지 모르겠다는 건데요, PC에 **[Git](https://git-scm.com/)**이 설치되어 있지 않아서 컴퓨터가 명령을 이해하지 못한 것입니다. 우선 Git을 설치해야겠네요.

> Git을 아직 설치하지 않으셨다면 **[여기](https://tired-o.github.io/)**를 참고하셔서 설치 후 이어서 진행해주세요.

git이 설치되어 있다면 아래와 같은 내용이 나올 겁니다.

`|   |   | |---|---| ||C:\Users\kiyun\git>git clone https://github.com/ita-bility/ita-bility.github.io<br>Cloning into 'ita-bility.github.io'...<br>remote: Enumerating objects: 3, done.<br>remote: Counting objects: 100% (3/3), done.<br>remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0<br>Receiving objects: 100% (3/3), done.|`

그리고 해당 경로로 가보면 파일이 잘 복사되어 있는걸 확인할 수 있습니다.

## 4. 로컬 Git에 새로운 파일 생성하기[](https://tired-o.github.io/posts/github-blog-1/#4-%EB%A1%9C%EC%BB%AC-git%EC%97%90-%EC%83%88%EB%A1%9C%EC%9A%B4-%ED%8C%8C%EC%9D%BC-%EC%83%9D%EC%84%B1%ED%95%98%EA%B8%B0)

로컬 Git에 새로운 파일을 만들어 보겠습니다. 폴더 안에 새 텍스트 파일을 만들고 **[Hello world](https://ko.wikipedia.org/wiki/%22Hello,_World!%22_%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%A8)**를 입력한 뒤 저장합니다. 파일명은 `Hello world.html`로 하겠습니다. 그리고 파일 확장자를 `txt`에서 `html`로 바꿔줍니다.

[![](https://tired-o.github.io/assets/img/2022-07-05/2022-07-05-github-blog-1-create_html.png)](https://tired-o.github.io/assets/img/2022-07-05/2022-07-05-github-blog-1-create_html.png "확장명을 변경해도 사용할 수 있으니 바꿔주세요.")_확장명을 변경해도 사용할 수 있으니 바꿔주세요._

파일을 실행하면 웹브라우저에 Hello world가 떠있는 화면이 보이실 겁니다.

## 5. GitHub에 수정사항 반영하기[](https://tired-o.github.io/posts/github-blog-1/#5-github%EC%97%90-%EC%88%98%EC%A0%95%EC%82%AC%ED%95%AD-%EB%B0%98%EC%98%81%ED%95%98%EA%B8%B0)

`Hello world.html` 파일을 만들었지만 로컬 PC에만 만들어졌을 뿐입니다. 작업한 내용을 GitHub에 저장하기 위해 아래 순서대로 진행해 보겠습니다.

1. 변경사항 저장
2. 변경사항 확정
3. 원격 저장소에 업로드

### 1. 변경사항 저장[](https://tired-o.github.io/posts/github-blog-1/#1-%EB%B3%80%EA%B2%BD%EC%82%AC%ED%95%AD-%EC%A0%80%EC%9E%A5)

변경사항을 저장하기 위해 명령 프롬프트로 돌아가 아래와 같이 입력합니다.

`|   |   | |---|---| ||C:\Users\kiyun\git>cd ita-bility.github.io<br>C:\Users\kiyun\git\ita-bility.github.io>git add -A|`

변경사항을 staging(저장을 확정하기 전 중간 단계)에 저장하되, 변경된 모든(`-A`, All) 내용을 저장한다는 명령어입니다.

### 2. 변경사항 확정[](https://tired-o.github.io/posts/github-blog-1/#2-%EB%B3%80%EA%B2%BD%EC%82%AC%ED%95%AD-%ED%99%95%EC%A0%95)

앞서 저장한 변경사항을 그대로 올릴 것이니 확정하겠습니다.

`|   |   | |---|---| ||C:\Users\kiyun\ita-bility.github.io>git commit -m "first commit"<br>[main af26d4c] first commit<br> 1 file changed, 1 insertion(+)<br> create mode 100644 Hello world.html|`

`commit`은 변경사항을 확정하는 것으로 변경사항에 대한 커멘트를 남겨(`-m "메시지"`) 나중에 무엇때문에 변경사항이 발생했는지 보기 쉽게 해줍니다.

### 3. 원격 저장소에 업로드[](https://tired-o.github.io/posts/github-blog-1/#3-%EC%9B%90%EA%B2%A9-%EC%A0%80%EC%9E%A5%EC%86%8C%EC%97%90-%EC%97%85%EB%A1%9C%EB%93%9C)

이제 `push` 명령어로 GitHub 저장소에 업로드 하겠습니다.

`|   |   | |---|---| ||C:\Users\kiyun\ita-bility.github.io>git push<br>info: please complete authentication in your browser...|`

업로드가 바로 될 줄 알았는데, 아래 화면처럼 팝업창이 뜹니다. Sign in with your browser를 눌러 GitHub에 로그인합니다.

[![](https://tired-o.github.io/assets/img/2022-07-05/2022-07-05-github-blog-1-git_push_login.png)](https://tired-o.github.io/assets/img/2022-07-05/2022-07-05-github-blog-1-git_push_login.png)

로그인을 하고 나니 추가 인증이 필요합니다. Authorize GitCredentialManager를 눌러 Git Credential Manager에 권한을 줍니다.

[![](https://tired-o.github.io/assets/img/2022-07-05/2022-07-05-github-blog-1-git_push_oauth.png)](https://tired-o.github.io/assets/img/2022-07-05/2022-07-05-github-blog-1-git_push_oauth.png)

Authorization confirm을 위해 GitHub 비밀번호를 다시 입력하면 Authentication Succeeded 화면이 뜨고 명령 프롬프트에서도 업로드가 완료된 것을 확인하실 수 있습니다.

[![](https://tired-o.github.io/assets/img/2022-07-05/2022-07-05-github-blog-1-git_push_oauth_success.png)](https://tired-o.github.io/assets/img/2022-07-05/2022-07-05-github-blog-1-git_push_oauth_success.png "인증 완료 화면")_인증 완료 화면_

`|   |   | |---|---| ||C:\Users\kiyun\ita-bility.github.io>git push<br>info: please complete authentication in your browser...<br>Enumerating objects: 4, done.<br>Counting objects: 100% (4/4), done.<br>Delta compression using up to 4 threads<br>Compressing objects: 100% (2/2), done.<br>Writing objects: 100% (3/3), 294 bytes \| 147.00 KiB/s, done.<br>Total 3 (delta 0), reused 0 (delta 0), pack-reused 0<br>To https://github.com/ita-bility/ita-bility.github.io.git<br>a17b2cb..af26d4c  main -> main|`

GitHub 저장소에도 `Hello world.html` 파일이 추가된 것을 확인할 수 있습니다.

[![](https://tired-o.github.io/assets/img/2022-07-05/2022-07-05-github-blog-1-github_update.png)](https://tired-o.github.io/assets/img/2022-07-05/2022-07-05-github-blog-1-github_update.png "Hello world.html 파일이 “first commit” 메시지와 함께 추가됐네요.")_Hello world.html 파일이 “first commit” 메시지와 함께 추가됐네요._
