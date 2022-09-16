## 220916 TIL


### 오늘 배운 것
- revert
- git collaborationn

### 배운 내용 정리

#### Rename
- worst
`$ mv server.py main.py` -> deleted, new file
- Best
`$ git mv server.py main.py` -> renamed

#### Undo
- git restore {fileName} : 해당파일 변경내용 되돌림
- git restore . : 현재 디렉토리 아래로 모든 변화를 취소하고 원래대로 돌아감

#### Unstaging
- git reset HEAD {fileName} : 스테이징된 파일 언스테이징

#### Edit lastest commit
- git commit -amend "" : 직전의 커밋 내용 수정

#### Reset vs Revert
**Reset**
- ex) `$ git reset --hard HEAD~3`
- worst
- 협업 시 다른 cloned repo에 존재하던 commit log에 의해 파일이 살아날 수 있음
- 과거 이력이 사라져 commit log tracking이 힘들어진다.
- 실수했을 경우 이를 기록하고 수정한 이력을 남길 것!!!

**Revert**
- ex) `$ git revert --no-commit HEAD~3..`
- best
- 잘못하기 전 과거로 돌아가 최신을 유지하면서 되돌렸다는 이력을 commit으로 남겨 모든 팀원들이 이 상황을 공유가능
