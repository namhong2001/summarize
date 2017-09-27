마크다운을 바로 볼 수 있는 vim plugin
========

## 설치
	npm install -g livedown
	git clone git://github.com/shime/vim-livedown.git ~/.vim/bundle/vim-livedown
bundle 에다가 넣는 방식은[vim-pathogen]을 쓰는 방식이다. 
따라서 미리 [vim-pathogen]을 설치해둔다.

## 사용법
	:LivedownToggle
command-line mode에서 이 명령어를 치면 새창이 뜨고 markdown의 preview를 볼 수 있다. 
저장할 때마다 새로고침 된다. 
하지만 매번 이 긴것을 칠 수는 없으니 *.vimrc*에 다음 내용을 넣어준다.

	cmap md LivedownToggle	
이 명령어는 command-line mode에서 md를 입력하면 LivedownToggle을 입력해주겠다는 말이다.

## 참고
[vim-livedown]
[vim-pathogen]

[vim-livedown]: https://github.com/shime/vim-livedown "vim-livedown"
[vim-pathogen]: https://github.com/tpope/vim-pathogen "vim-pathogen"
