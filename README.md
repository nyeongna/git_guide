# 📖 깃 사용 가이드 (git_guide)
## 깃 사용시 궁금했던 점 정리


## git push / pull
### [이슈]
- git push의 정확한 의미가 무엇인가?
- git pull의 정확한 의미가 무엇인가?

### [답변]
- git push의 정확한 의미가 무엇인가?
>- git push는 정확하게 말하면, *push를 하려는* branch의 commit 상황을 *push를 당하는* branch에 밀어넣는 액션이다. <br>
밀어넣을 때는 당연히 두 branch의 전체적인 commit 상황이 같아야 하고, <br>
같은 파일에 대해서 commit 상황이 다른 파일이 있다면 *push 하려는* branch가 우선시 된다. 따라서, push 당하는 branch는 변경점이 있으면 안된다 (있으면 conflict)
conflict이 나는 이유는 git이 같은 파일에 대한 다른 commit 중 어느 것을 따라야 하는지 알 수 없기 때문이다.

- git pull의 정확한 의미가 무엇인가?
>- git pull은 정확히 git fetch + merge 이다. git fecth는 단순히 소스 reposit에서 commit 들을 가져오는 행위에 해당하고 <br>
merge는 가져온 commit과 합치려는 branch의 commit을 한군데로 합치는 것을 의미한다. (합치는 과정에서 git이 헷갈릴만한 상황이 발생하면 issue/conflict 발생) <br>
다시 말해, git pull 은 소스 branch가 주권이 있어서 여기에 기준을 맞춰서 merge를 진행한다. (동일 파일에 대해 변경점이 있다면 소스 branch의 변경점을 따른다)

## Conflict이 나는 기준은 무엇인가?
### [이슈] 
>- Remote reposit A 생성 →
>- remote A 에서 a.txt 생성 후 commit →
>- local 에서 reposit A clone →
>- remote A 에서 b.txt 생성 후 commit
>- local A 에서 c.txt 생성 후 commit
- 여기서 local A 에서 remote A로 push 하려고 하면 과연 conflict이 나는가?
- conflict이 난다면 local A에 없고 remote A에 존재하는 b.txt 때문인가? 아니면 반대인 c.txt 때문인가?

### [답변]
- 여기서 local A 에서 remote A로 push 하려고 하면 과연 conflict이 나는가?
>- 맞다. conflict이 난다. git push를 하기 전에는 git pull(fetch+merge) 를 통해 push 하는 branch와 push 당하는 branch의 commit 상황을 맞출 필요가 있다 <br>
local A는 git이 a.txt 와 c.txt 파일들을 트래킹 중이며, remote A는 git이 a.txt와 b.txt 에 대해 트래킹 중이다. 고로 전체적인 commit 상황이 같지 않으므로 push가 불가능하다
- 그렇다면 git pull 은 issue가 나지 않는가?
>- 아니다. issue가 난다. 마찬가지로 local A는 a.txt 와 c.txt를 remote A는 a.txt 와 b.txt 를 트래킹중이므로 파일 트래킹에 대한 conflict은 없지만 전체적인 commit 상황이 다르므로 issue가 발생한다고 볼 수 있다. 하지만 파일 conflict이 아니므로 git의 기본설정을 바꿔서 rebase 자동 기능 (git config pull.rebase true)을 키면 git이 자동으로 issue가 난 부분을 rebase 하고 merge를 시켜주면서 pull을 해준다.
                                                                                                                          
