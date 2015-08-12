일시 : 2013.10.30 수 11:00~
발재자 : 이정훈

주제 : Git

민규의 단상

Git와 SVN의 기능상의 차이점은 사실상 거의 없는 것 같습니다.
단, 로컬 저장소의 개념을 가진 Git가 좀 더 다양한 개발 시나리오를 커버할 수 있을 것 같습니다. 중앙의 소스저장소에 빌드를 깨지않고도 로컬에서 소스 형상관리를 하면서 개발할 수 있는거죠.

하지만, 개발 커뮤니티에서 이 두 시스템이 어떻게 받아들여지느냐는 관점에서 봤을때 두 시스템의 차이점이 확연히 드러나는데요. SVN이 종자(Seed)를 관리하듯이 소스코드를 접근하는 반면, Git는 자연상태의 유전적 진화 방식을 따르고 있다고 보여집니다. SVN이 통제/관리적 방식으로 소스코드를 관리한다면, Git는 자연적인 상태에서 유전적으로 변이가 생기도록 한 뒤 뛰어난 변이들을 머지하는 방식으로 사용되고 있는 것 같습니다.





---

참조
Socialinus의 "SVN 능력자를 위한 git 개념 가이드"

http://www.slideshare.net/einsub/svn-git-17386752‎

(사내에서는 슬라이드셰어가 막혀있네요)