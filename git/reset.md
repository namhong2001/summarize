Git reset
===============
HEAD는 보통 특정 branch를 가리킨다.
branch는 특정 commit을 가리키는데(Refs) 대부분 해당 브랜치에서 가장 최근의 커밋이다.
reset으로 변경하는 것은 HEAD자신이 아니라 branch가 가리키는 commit을 변경하는 것이다.

## git reset --soft
HEAD branch 가 가리키는 커밋을 지정된 커밋으로 변경한다.

    git reset --soft HEAD~

여기서 *HEAD~* 는 HEAD의 부모 commit을 말한다

## git reset --mixed
HEAD branch가 가리키는 커밋을 지정된 커밋으로 변경하고 *Index*또한 해당 커밋 내용으로 변경한다.
여기서 *Index*란 Staging 상태라고 볼 수 있다.

    git reset --mixed HEAD~
    
--mixed 가 Default다.

## git reset --hard
HEAD branch가 가리키는 커밋을 지정된 커밋으로 변경하고, *Index*를 변경하고 *Working Directory*에 덮어쓰기까지 한다.

    git reset --hard HEAD~

*--hard* 옵션을 줄때는 조심해야 한다 *Working Directory*의 파일들을 덮어쓰기 때문에 git에 커밋이 되지 않았다면 이전 내용을 복구할 방법이 없다

## git reset file.txt
reset 명령을 실행할 때 경로를 지정하면 1단계를 건너뛰고 정해진 경로의 파일에만 나머지 reset 단계를 적용한다. 
이는 당연한 이야기다. HEAD는 포인터인데 경로에 따라 파일별로 기준이 되는 커밋을 부분적으로 적용하는 건 불가능하다. 
하지만, Index나 워킹 디렉토리는 일부분만 갱신할 수 있다. 따라서 2, 3단계는 가능하다.

예를들어 `git reset file.txt` 명령은 `git reset --mixed HEAD file.txt`인데,
이 명령을 실행하면 가리키는 commit은 변경하지 않고,
지정된 경로만 Index를 HEAD가 가리키는 상태로 만든다.
HEAD의 상태와 동일하게 만드는 거니 곧 Index를 초기 상태로 돌리는 것이고, 즉 해당 파일을 unstaged 상태로 만드는 것이다.
git add 명령과 정확히 반대의 일을 한다.

예를 하나 더 들면, `git reset --mixded HEAD~10 file.txt`는
HEAD로부터 10단계 전의 commit의 file.txt를 Index에 반영시킨다.

또 다른 예로, `git reset --soft HEAD~10 file.txt`는 오류가 난다.

## Squash
이전 커밋으로 돌아가 commit을 하면 새로운 커밋이 생성이 되고 이전의 커밋은 더이상 히스토리에 보이지 않는다.
아마 이 커밋들도 볼 수 있는 방법이 있을 테지만 branch의 히스토리에는 보이지 않으니 버려졌다고 보아도 무방한 듯 하다.
이런 방식으로 이전의 커밋을 지우고 히스토리를 재단장 하기 위해, 지저분한 커밋들을 합치기 위해

    git reset --soft HEAD~2
    git commit
    
을 사용할 수 있다. 

## Checkout
`git checkout [commit] file`은 `git reset --hard [commit] file`과 같다.

## Conclusion
-| HEAD | Index | Workdir | WD(Working Directory) Safe?
---|---|---|---|---
**Commit Level** ||||
`reset --soft [commit]` | REF | NO | NO | YES
`reset [commit]` | REF | YES | NO | YES
`reset --hard [commit]` | REF | YES | YES | **NO**
`checkout <commit>` | HEAD | YES | YES | YES
**File Level** | | | |
`reset [commit] <paths>` | NO | YES | NO | YES
`checkout [commit] <paths>` | NO | YES | YES | **NO**

* REF - HEAD가 가리키는 브랜치를 움직임
* HEAD - HEAD자체가 움직임

WD Safe가 NO 이면 commit하지 않은 내용이 안전하지 않기 때문에 실행할 때 조심해야 한다.

## 참고
<https://git-scm.com/book/ko/v2/Git-%EB%8F%84%EA%B5%AC-Reset-%EB%AA%85%ED%99%95%ED%9E%88-%EC%95%8C%EA%B3%A0-%EA%B0%80%EA%B8%B0>