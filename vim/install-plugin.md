플러그인 설치
===================

[vim-pathogen] 을 쓰면 vim 플러그인 설치가 쉽다고 한다.
링크를 따라가서 그대로 적용

	mkdir -p ~/.vim/autoload ~/.vim/bundle && \
	curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim

이걸 그대로 복붙한다. 그리고 .vimrc에 다음 사항을 추가해준다.

	execute pathogen#infect()
	syntax on
	filetype plugin indent on

현재 내 .vimrc는 다음과 같다.

	execute pathogen#infect()
	syntax on
	filetype plugin indent on
	cmap md LivedownToggle

## 참고
[vim-pathogen]


[vim-pathogen]: https://github.com/tpope/vim-pathogen "vim-pathogen"
