# inode


- Linux/Unix의 파일 시스템에서 사용되는 자료구조를 말한다.

- 모든 파일이나 디렉토리에는 1개의 inode를 가지고있다.(1개의 inode는 64byte로 이루어짐)

- 각 inode에는 해당 파일의 소유권, 허가권, 파일 종류등의 정보, 해당 파일의 실제 데이터가 

  어디에 있는지 위치(=주소)도 가지고 있다.


- inode가 모여있는 공간이 inode블록이다. (전체 디스크의 1%정도를 차지한다.)

  실제 데이터가 저장되어 있는 디스크 공간으로 전체 디스크의 대부분을 차지함
