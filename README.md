# ros2-ws
ros2 개발 환경을 구성하는 제일 기초적인 부분. 사용 방법은 다음과 같다.

## 리눅스에서.
1. docker를 설치한다.
2. vscode를 설치한다.
3. vscode에서 devcontainer, Remote Development 확장을 깐다.
4. 이 레포지토리를 clone한다.
5. 레포지토리를 vscode로 연다.
6. `Ctrl + Shift + P`로 vscode 명령창을 열어 rebuild 검색. Rebuild Container 실행

## 윈도우에서.
1. wsl2를 깐다.(되도록 윈도우 11이면 좋다. 이유는 후술.)
2. wsl2에 우분투 설치.
3. wsl2 내부에 docker를 설치한다.(윈도우 위에 깔기 위해 docker desktop을 까는 것과 다르다.)
    ```shell
    curl -fsSL https://get.docker.com -o get-docker.sh
    sudo sh ./get-docker.sh
    ```
    [출처](https://docs.docker.com/engine/install/ubuntu/)
4. vscode를 설치(윈도우에).
5. vscode에서 devcontainer, Remote Development 확장을 깐다.    
6. 이 레포지토리를 wsl에 clone.
7. 레포지토리를 clone한 디렉토리를 vscode로 연다. `code .`
8. `Ctrl + Shift + P`로 vscode 명령창을 열어 rebuild 검색. Rebuild Container 실행

### 만약 docker desktop이 이미 깔려있는 경우.
1. docker desktop 삭제.
2. wsl이 있다면 wsl안의 `~/`에 있는 docker 관련 파일 삭제.
3. 위의 단계 적절히 시작(당연히 wsl을 지울 필요는 없음.)


## 네트워크 설정
ROS2는 같은 서브넷 안에 있는 모든 ROS2 노드들 끼리 통신이 가능하다. 이를 위한 설정.
### 리눅스에서.
이미 옵션을 `devcontainer.json`에 넣었으니 따로 할 건 없다.
### 윈도우에서.
이 기능은 윈도우 11에서만 된다.
1. `C:\Users\<사용자 이름>` 안에 `.wslconfig`파일을 만든다.
2. 그 안에 다음과 같이 wsl 옵션을 준다. 이 옵션은 wsl이 미러링 모드로 동작하도록 한다. 미러링 모드는 wsl의 ip가 호스트의 ip와 같아지도록 한다.
    ```txt
    [wsl2]

    networkingMode=mirrored
    ```
    [출처](https://learn.microsoft.com/ko-kr/windows/wsl/wsl-config)
3. wsl이 켜져있으면 껐다 켠다.  
4. 나머지 wsl상에서 할 것은 리눅스와 동일하다.