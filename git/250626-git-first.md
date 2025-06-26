# Git 

## 250626

### Git : 분산버전 관리 시스템 


## 기본개념

``` 
저장소 Repositor : 프로젝트의 모든 파일과 변경 이력이 저장되는 공간
커밋 commit : 변경사항을 저장소에 최종 기록하는 행위
브랜치 Branch : 독립적으로 새로운 기능 개발, 실험가능한 공간
병합 Merge : 서로 다른 브랜치의 변경사항을 합치는 과정

```

# Git & GitHub 

## 1. Shell 기본 명령어

```
ls                    # 파일 목록 보기ls :  list
cd Document           # 폴더 이동 cd :  change directory
mkdir dev             # 폴더 생성 
pwd                   # 현재 위치 확인 pwd  present working directory
touch newfile.md      # 빈 파일 생성 touch
mv file.md temp/      # 파일 이동 mv : move
cp file.md copy.md    # 파일 복사 cp : copy
rm file.md            # 파일 삭제 rm : remove
rm -rf temp           # 폴더 삭제 rm -rf 파일 삭제 후 폴더 삭제
cat file.md           # 파일 내용 보기 

```

## 2. Vim 에디터

```bash
vi filename.md        # vim으로 파일 열기

```

### Vim 모드

- **Normal 모드** (기본): 명령어 입력
- **Insert 모드** (`i`): 텍스트 입력
- **Visual 모드** (`v`): 텍스트 선택
- **Command 모드** (`:`): 저장/종료 등

### Vim 명령어

```
# Normal 모드
h j k l      # 왼쪽, 아래, 위, 오른쪽 이동
i            # Insert 모드
v            # Visual 모드
ESC          # Normal 모드로 돌아가기
dd           # 한 줄 삭제
yy           # 한 줄 복사
p            # 붙여넣기
u            # 실행취소

# Command 모드
:q           # 종료
:q!          # 강제 종료
:w           # 저장
:wq          # 저장 후 종료
:20          # 20번째 줄로 이동
:set nu      # 줄 번호 표시




## Conventional Commits
- [Conventional Commits](https://www.conventionalcommits.org/ko/v1.0.0/)
- 명확한 커밋 히스토리를 생성하기 위한 간단한 규칙
- prefix 종류
	- feat : 기능 개발 관련
	- fix : 오류 개선 혹은 버그 패치
	- docs : 문서화 작업
	- conf : 환경설정 관련

## .gitignore
- Git에서 **버전 관리하지 않을 파일이나 폴더, 파일 패턴**을 지정하는 설정 파일
- [Toptal](https://www.toptal.com/developers/gitignore/)에서 원하는 설정에 맞는 .gitignore 파일 생성이 가능

## pre-commit
- commit 수행  전  체크해야  할  것들을  자동수행하도록  도와주는  도구
```shell
# MacOS 환경에서 실습

$ pip --version # pip 존재 확인
$ pip install pre-commit # 설치
$ pre-commit -V # 명령어 존재 확인
$ pre-commit sample-config > .pre-commit-config.yaml # 샘플 설정 만들기 $ pre-commit run # 실행 확인
```
- 설치 후 바로 실행이 되지 않아 환경변수 설정 추가
```shell
$ sudo vim ~/.zshrc
# export PATH="$HOME/.local/bin:$PATH" 추가 후
$ ource ~/.zshrc # 실행
```

```

## 3. Markdown 문법

```markdown
# 제목 (h1~h6)
## 소제목

**굵은 글씨**
*기울임 글씨*
`단일 코드`
~~취소선~~

- 순서없는 목록
- 목록 2

1. 순서있는 목록
2. 목록 2

[링크 텍스트](링크 주소)
![이미지 설명](이미지 주소)

```python
# 코드 블록
print('hello')

```

```

## 4. Git 기본 설정
```bash
git config --global user.name "your-name"
git config --global user.email "your-email@example.com"
git config --global core.editor "vim"
git config --global core.pager "cat"
git config --list

```

## 5. Git 기본 워크플로우

```bash
# 저장소 복제
git clone https://github.com/username/repo-name.git
cd repo-name

# 파일 수정 후
git status              # 상태 확인
git add filename        # 특정 파일 스테이징
git add .              # 모든 파일 스테이징
git commit -m "메시지"  # 커밋
git push origin main   # 원격 저장소에 푸시

```

## 6. Git 브랜치 관리

```bash
# 브랜치 확인
git branch          # 로컬 브랜치
git branch -r       # 원격 브랜치
git branch -a       # 모든 브랜치

# 브랜치 생성 및 전환
git branch feature-name     # 브랜치 생성
git switch feature-name     # 브랜치 전환
git switch -c feature-name  # 생성 + 전환

# 브랜치 병합
git switch main
git merge feature-name

# 브랜치 삭제
git branch -D feature-name

# 원격 브랜치 푸시
git push -u origin feature-name  # 첫 푸시
git push                        # 이후 푸시

```

## 7. Commit 메시지 컨벤션

```
feat: 새로운 기능 추가
fix: 버그 수정
docs: 문서 수정
test: 테스트 추가
conf: 설정 변경
build: 빌드 시스템 수정
ci: CI/CD 설정
chore: 기타 작업
style: 코드 스타일 수정
refactor: 코드 리팩토링

예시:
feat: add user login component
fix: resolve navigation bug
docs: update README installation guide

```

## 8. Git 문제 해결

```bash
# 작업 디렉토리 변경사항 되돌리기
git restore filename
git restore .

# 스테이징 취소
git reset HEAD filename

# 커밋 메시지 수정
git commit --amend

# 커밋 되돌리기 (위험!)
git reset --hard HEAD~1

# 안전한 되돌리기
git revert HEAD

# 임시 저장
git stash                # 현재 작업 임시 저장
git stash pop           # 임시 저장 복원
git stash list          # stash 목록

```

## 9. Merge Conflict 해결

```bash
# 충돌 발생시
git merge main
# 충돌 파일 편집 (<<<<<<, ======, >>>>>> 부분 수정)
git add filename
git commit

# 또는 rebase 사용
git rebase main
# 충돌 해결 후
git add filename
git rebase --continue

```

## 10. Pre-commit 설정

```bash
pip install pre-commit
touch .pre-commit-config.yaml
# 설정 파일 작성 후
pre-commit install
pre-commit run --all-files

```

## 11. Git Flow 전략

### Git Flow

```
master (배포)
├── develop (개발)
├── feature/기능명 (기능 개발)
├── release/버전명 (배포 준비)
└── hotfix/버그명 (긴급 수정)

```

### GitHub Flow (간단)

```
main (배포)
└── feature/기능명 (기능 개발) → Pull Request

```

### GitLab Flow

```
master (메인)
├── feature/기능명 (기능 개발)
├── pre-production (테스트)
└── production (배포)

```

## 12. GitHub 협업 워크플로우

### Fork 방식

1. **Fork** → 원본 저장소 복사
2. **Clone** → 로컬에 복제
3. **Branch** → 기능 브랜치 생성
4. **Commit** → 작업 후 커밋
5. **Push** → 포크 저장소에 푸시
6. **Pull Request** → 원본에 병합 요청

```bash
# upstream 설정
git remote add upstream https://github.com/original/repo.git
git fetch upstream
git merge upstream/main

```

## 13. GitHub Issues & Projects

```markdown
## Issue Template
### Description
문제 설명

### Tasks
- [ ] 할 일 1
- [ ] 할 일 2

### References
- [링크](주소)

```

### Issue Labels

- **Type**: Bug, Enhancement, Question
- **Priority**: High, Medium, Low
- **Status**: In Progress, Review Needed, Done

## 14. Pull Request Template

```markdown
## Summary
변경사항 요약

## Proposed Changes
- close #이슈번호 (이슈 닫기)
- fix #이슈번호 (버그 수정)
- resolves #이슈번호 (문제 해결)

## To Reviewers
리뷰어에게 전달할 내용

```

## 15. .gitignore 예시

```
# OS
.DS_Store
Thumbs.db

# Python
__pycache__/
*.pyc
*.pyo
.env

# Node.js
node_modules/

# IDE
.vscode/
.idea/

```

## 16. README.md 구조

```markdown
# 프로젝트명
프로젝트 설명 [Demo](링크)

## Prerequisites
필요한 것들

## Installation
설치 방법

## Features
주요 기능

## Usage
사용 방법

## Contributing
기여 방법

## License
라이선스

```

## 핵심 포인트

1. **기본 흐름**: `add → commit → push`
2. **브랜치 전략**: 기능별로 브랜치 생성
3. **커밋 메시지**: 컨벤션 따르기
4. **협업**: Fork → PR → Code Review
5. **문제 해결**: stash, restore, revert 활용

## 주의사항

- `git reset --hard`는 복구 불가능
- `git push -f`는 팀 작업시 위험
- 민감한 정보는 `.gitignore`에 추가
- 충돌 해결시 꼼꼼히 확인
- Personal Access Token 사용 (GitHub)
