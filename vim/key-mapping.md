vim 에서 custom 단축키나 명령어를 설정하는 방법
==================

*.vimrc* 같은데서 nmap(normal mode mapping), cmap(command-line mode mapping) 등을 이용해 설정할 수 있다

예를들어 내 *.vimrc* 는 다음과 같은 설정을 가지고 있는데

    execute pathogen#infect()
    syntax on
    filetype plugin indent on
    cmap md LivedownToggle

여기서 *cmap md LivedownToggle*은 command-line mode에서 md를 누르면 LivedownToggle로 바꿔달라 가 된다.
따라서 다음과 같이 입력하면
    
    :md
    
아래와 같이 바뀐다

    :LivedownToggle

좀더 자세한 정보는 [vimrc-configuration]를 보도록 한다
    
         


## 참고
[vimrc-configuration]


[vimrc-configuration]: http://jaeheeship.github.io/console/2013/11/15/vimrc-configuration.html "참고"