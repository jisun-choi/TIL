### GIT history 조작(?) 명령어 모음

## Reset

```
#모든 커밋 로그를 확인하는 명령어
git reflog
```

- `git reset --hard <커밋명>`:
  - 돌아가려는 커밋 이후에 작성된 내용을 모두 지움
- `git reset --soft <커밋명>`:
  - 돌아가려는 커밋으로 돌아가지만 이후 작성된 내용과 인덱스가 그대로 남아있어서 바로 다시 커밋할 수 있는 상태가 됨
- `git reset --mixed <커밋명>`:
  - 리셋 옵션 적지 않으면 디폴트로 mixed 로 실행 됨
  - 돌아가려는 커밋 이후 내용은 그대로 남지만 인덱스는 초기화 됨 (다시 git add <파일명> 해줘야 함)
- `git reset HEAD~n`:
  - 현재로부터 n개 이전 이력으로 돌아가라는 명령어

**주의사항**
이미 원격저장소에 올라간 커밋을 리셋할 경우, 다른 팀원들이 해당 브랜지를 이미 pull 받았다면 다른 사람들의 로컬 저장소의 커밋까지 reset 할 수 없어서 수동 삭제 해줘야함

## Revert

특정 커밋을 되돌리는 작업을 하나의 커밋으로 간주하여 커밋 히스토리에 추가<br>
b + (-b) = 0 의 개념으로 추가했던 b를 없애는 것
`git revert <커밋명>`