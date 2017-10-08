Hunks
========
Hunk는 한 덩어리 라는 의미인데 git에서는 한 파일의 변경사항중 각각의 덩어리를 의미한다.
`--patch`또는 `-p`라는 옵션을 통해서 파일 단위가 아닌 hunk 단위별로 명령을 수행할 수 있다.
예를들어

    git add -p .
    
를 수행하면 interactive 화면이 뜨며, 이 화면에서 보여진 hunk를 *Index*에 추가할지 말지를 결정할 수 있다.


## 참고
<https://www.bignerdranch.com/blog/using-git-hunks/>