# SvnToGit
SVN에서 GIT으로 전환하기 

# 1. SVN 사용자 정보 .txt 파일에 저장 #

### 1.1 svn-migration-scripts.jar 파일 다운로드 ###
 - LINK : https://bitbucket.org/atlassian/svn-migration-scripts/downloads/
 - 다운받은 파일 (.jar) 은 아무 데나 상관없이 저장한다.
 
### 1.2 authors.txt 파일 추출 ###
 - 커맨드 실행에서 실행 java -jar svn-migration-scripts.jar authors  <SVN경로> > authors.txt
 - ex) java -jar svn-migration-scripts.jar authors  https://DESKTOP-1HTU111/svn/project/ > authors.txt
 - 실행하면 authors.txt  파일생김
 - authors.txt 파일에 SVN 사용자 정보가 들어있음 ( 커밋한 사용자 정보 )
 
### 1.3. SVN의 Commiter 정보 수정
  - 사용자의 정보들이 나온다. 
  - ex) orange = orange <oltop@naver.com>
  - 왜 그런지 모르겠는데 모르는 사용자 정보도 나왔다. 
  - 모르는 사용자들은 있는 데로 냅두고 이코르(=) 기준으로 왼쪽 정보는 냅두고 오른쪽 정보는 ID <git아이디> 로 변경한다.
  
  
# 2. 저장소 내려받기 #

 ### 2.1 저장소 내려받기 ###
  - 커맨드에서 실행 git svn clone --stdlayout --authors-file=authors.txt http://svn.example.com/project --username {username} {directory}
  - ex) git svn clone --stdlayout --authors-file=authors.txt https://DESKTOP-1HTU523/svn/svn_project/ --username orange601 https://emailID@bitbucket.org/path/project.git
  
# 3. SVN Clean #

 ### 3.1 SVN clean ###
  - java -Dfile.encoding=utf-8 -jar ../svn-migration-scripts.jar clean-git --force
  
# 4. git commit #
  
 ### 4.1 이전할 git 저장소에 커밋(push) 하기 (git 서버 저장소가 git.example.com/project)인 경우 ###
  - git remote add origin http://{username}@git.example.com/project
  - git push origin master
  - git 저장소의 사용자 이름이 {username}일 경우이며 비밀번호를 물어보는데 맞으면 커밋이 완료됩니다. 
  - 이제 git 서버 저장소에서 project 안에 기본 브랜치인 master에 소스가 커밋된 것을 확인할 수 있을 것입니다.


 ### 4.2 <tip.1>master에 이미 내용이 있어서 덮어 씌우기 위해서는 다음 명령을 실행합니다. ###
  - git push origin +master

 ### 4.3 <tip.2>master가 아닌 다른 브랜치에 커밋하기 위해서는 다음 명령을 실행합니다. ({branchname}은 서버에 생성 할 새로운 브랜치 이름입니다.) ###
  - git push origin master:{branchname}
