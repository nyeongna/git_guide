# 📖 깃 사용 가이드 (git_guide)
## 깃 사용시 궁금했던 점 정리

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
ㅁㄴㅇㅁㄴㅇ
