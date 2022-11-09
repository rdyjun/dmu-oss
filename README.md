# git-command
깃 수업을 통한 커맨드 정리

### git diff

```bash
git diff           # wd와 sa의 차이 확인
git diff HEAD      # wd와 head 커밋 차이 확인
git diff --cached  # sa와 head 커밋 차이 확인
git diff --staged  # cached와 동일
```

## 9주차

### git stash

커밋할 필요 없이 파일의 변경 사항을 숨기거나 비밀리에 저장할 수 있는 도구

- `git log --all` 로 확인 시 stash 정보도 나온다.

```bash
git stash                    # wa, sa 임시 저장 및 wd, sa 수정 사항 지우기
git stash -u                 # untracked 파일까지 임시 저장
git stash list               # stash 목록 확인
git stash show               # stash와 현재 디렉터리의 차이
git stash show -p            # 차이를 더 자세히 보기
git stash show -p stash@{1}  # 1번째 index의 stash 와 wd 차이 보기

# pop
git stash pop                # 임시로 저장한 wd 불러오기 (stash 목록에서 빠짐)
git stash pop --index        # wd와 sa 까지 이동 적용

# apply
git stash apply              # 임시로 저장한 wd 불러오기 (stash 목록 유지)
git stash apply --index      # wd와 sa 까지 복사 적용

# keep index
git stash --keep-index       # sa는 유지하고 wd만 복사함

git stash branch [브랜치명]    # 브랜치 생성 및 해당 브랜치에 wd, sa, ut 복사

git stash clear              # stash list 삭제
```

### git clean

```bash
git clean     # ut 파일 삭제 (삭제 안됨)
git clean -f  # ut 파일 강제 삭제
git clean -n  # ut 파일 목록 확인g
git clean -i  # 대화모드로 삭제
# Would remove the following item:
# [삭제 목록]
# *** Commands ***
# 1: clean                2: filter by pattern    3: select by numbers
# 4: ask each             5: quit                 6: help
# What now>
```

# 10주차

## 병합 (merge)

```bash
git merge [브랜치명]  # 자동으로 3way, fast-forward 구분해서 실행
git merge [브랜치명] --no-ff  # 3way 방식으로 실행
```

### 3way
기본 브랜치 헤드의 위치가 파생된 브랜치의 조상 커밋이 아니라면, 3way로 자동 적용

- 새로운 해시 값이 부여됨

> 즉, 기본 브랜치와 파생된 브랜치에 각각 수정사항이 있다면 3way
> 파생된 브랜치에만 수정 사항이 있다면 fast-forward 자동 적용

><img width="280" alt="image" src="https://user-images.githubusercontent.com/45596014/200796640-9ccd2060-f89b-4281-9b42-8011c2d4efce.png">

### fast-forward
파생된 브랜치에만 수정 사항이 있다면 fast-forward 자동 적용

- 새 해시값 부여 안됨

> fast-forward 말고 3way 방식을 사용할 경우 
`git merge [브랜치명] --no-ff` 사용

<img width="280" alt="image" src="https://user-images.githubusercontent.com/45596014/200796797-d92e6fa1-b8ad-4cf4-9022-821c6d7e08b8.png">
