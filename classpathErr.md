# 2021 10 13 <br>이클립스 classpath 오류났을 때 대처법 
<br>
Project referenced by the classpath does not exist
The project: <project name> which is referenced by the classpath, does not exist. error in Eclipse

Resolution
Right click on the project from project explorer >> select build path >> configure build path >> a popup window will appear. Go to project tab and check the entry of project if that project is not in your eclipse project explorer then remove the project and apply the changes. 
(프로젝트 익스플로러에서 오른쪽 클릭 -> builed path 클릭 -> configure build path -> 새창이 뜸. -> 프로젝트 탭 -> 기존에 오류난 프로젝트 remove하고 본인 프로젝트 추가하고 저장.
Now build the project again.
