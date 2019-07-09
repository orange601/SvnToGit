# SvnToGit
SVN에서 GIT으로 전환하기 

# A. SVN 사용자 정보 .txt 파일에 저장 #

### 1. svn-migration-scripts.jar 파일 다운로드 ###
 - LINK : https://bitbucket.org/atlassian/svn-migration-scripts/downloads/
 - 다운받은 파일 (.jar) 은 아무 데나 상관없이 저장한다.
 
### 2. authors.txt 파일 추출 ###
 - 커맨드 실행에서 실행 java -jar svn-migration-scripts.jar authors  <SVN경로> > authors.txt
 - ex) java -jar svn-migration-scripts.jar authors  https://DESKTOP-1HTU111/svn/project/ > authors.txt
 - 실행하면 authors.txt  파일생김
 - authors.txt 파일에 SVN 사용자 정보가 들어있음 ( 커밋한 사용자 정보 )
 
### 3. SVN의 Commiter 정보 수정
  - 사용자의 정보들이 나온다. 
  - ex) orange = orange <oltop@naver.com>
  - 왜 그런지 모르겠는데 모르는 사용자 정보도 나왔다. 
  - 모르는 사용자들은 있는 데로 냅두고 이코르(=) 기준으로 왼쪽 정보는 냅두고 오른쪽 정보는 ID <git아이디> 로 변경한다.
  
  
# B. 설정 변경 #

 ### 1. 저장소 내려받기 ###
  - 커맨드에서 실행 git svn clone --stdlayout --authors-file=authors.txt http://svn.example.com/project --username {username} {directory}
  - ex) git svn clone --stdlayout --authors-file=authors.txt https://DESKTOP-1HTU523/svn/svn_project/ --username orange601 https://emailID@bitbucket.org/path/project.git
  
