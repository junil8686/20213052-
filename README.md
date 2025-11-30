# 20213052-
.# 과제#2: 리눅스 프로세스 관리 명령어 조사
학번: 20213052
이름: 박준일
##top 명령어 : #시스템의 프로세스/메모리/CPU 사용 현황을 실시간으로 모니터링하는 도구
- Windows 작업관리자와 유사한 역할
- <img width="1094" height="265" alt="image" src="https://github.com/user-attachments/assets/22b4da89-46ff-4ea2-a33f-12c36e40f691" />


함께 쓰이는 옵션
- top -d 1 ->	1초마다 갱신
- top -u -> 사용자명	특정 사용자 프로세스만 보기
- top -p <PID> -> 특정 프로세스만 모니터링
- top -n 5 -> 5번 갱신 후 종료
- 실행 결과
- 19:20:51 up 3 days, 5:38,  2 users,  load average: 0.32, 0.28, 0.10
- -> 시스템 시간 / 업타임 / 사용자 수 / Load Average(CPU코어 수보다 높으면 과부하)
- Tasks: 190 total, 1 running, 189 sleeping, 0 stopped, 0 zombie
-  - 사용중인 프로세스 1개 대기중인 프로세스 189개 좀비,정지프로세스 0
- %Cpu(s):  2.3 us,  1.0 sy,  0.0 ni, 96.0 id, 0.3 wa, 0.0 hi, 0.4 si, 0.0 st
- -> CPU사용률
- us	사용자 프로세스
- sy	시스템(커널) 작업
- ni	nice 값 조정된 프로세스
- id	idle
- wa	I/O 대기
- hi	하드웨어 인터럽트
- si	소프트웨어 인터럽트
- st	stolen time
- MiB Mem :  3918.2 total,  1200.0 used,  2500.0 free,  150.0 buff/cache
- MiB Swap:  2048.0 total,  300.0 used,  1748.0 free
- -> 메모리 사용량
-   PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
-     1 root      20   0    4628   3200   2944 S   0.0   0.0   0:00.04 bash
-    13 root      20   0    7316   3200   2688 R   0.0   0.0   0:00.05 top
- -> 프로세스 목록

- ps 명령어 : 현재 실행 중인 프로세스를 확인하는 명령어
- <img width="408" height="112" alt="image" src="https://github.com/user-attachments/assets/c5bffbfd-a149-4004-a1e2-7afe1200bd77" />
- 함께쓰는 옵션:
- -e	모든 프로세스
- -f	full format
- x   터미널 없는 프로세스도 표시

- 자주 쓰는 ps 명령어 예시
- ps -ef | grep nginx
- ps aux | grep python
- -> 특정 프로세스 검색
- ps -u ubuntu
- -> 특정 사용자 프로세스 검색
- ps -p <PID> -o ppid=
- -> 특정 PID의 부모 프로세스 확인

- ps 출력 의미
- PID	프로세스 ID
- PPID	부모 프로세스 ID
- UID / USER	실행 사용자
- %CPU	CPU 사용률
- %MEM	메모리 사용률
- VSZ	가상 메모리 사용량
- RSS	실제 메모리 사용량
- STAT	프로세스 상태 (R,S,D,T,Z 등)
- TIME	CPU 사용 시간
- CMD	실행 명령어

- ps  상태 코드
- R	Running(실행 중)
- S	Sleeping(대기)
- D	Disk sleep(I/O 기다리는 중)
- T	Stopped(중지됨)
- Z	Zombie
- W	Paging(거의 안 나옴)
- <	높은 우선순위
- N	낮은 우선순위


- jobs 명령어 : 현재 쉘에서 실행 중인 백그라운드 작업 & 중단된 작업 상황을 출력.
<img width="568" height="132" alt="image" src="https://github.com/user-attachments/assets/e05e8ef0-1329-4e52-ac28-8fd8cab532a6" />

- [1]+  Running    sleep 100 & ->
- [1]	     :         Job 번호
- + / -    :         기본 작업(+) / 차순위 작업(-)
- Running / Stopped	 상태
- sleep 100	         명령어


- kill 명령어 : 프로세스에 신호(Signal)를 보내서 종료하거나 특정 동작을 수행시키는 명령어
- 자주 쓰는 시그널
- 15	SIGTERM	정상 종료 요청 (기본)
- 9	  SIGKILL	강제 종료 (즉시 죽임)
- 2	  SIGINT	Ctrl + C 와 동일
- 19	SIGSTOP	일시정지 (Ctrl + Z와 유사)
- 18	SIGCONT	정지된 프로세스 재개

- 프로세스 이름으로 종료 : killall
- killall firefox -> firefox 프로세스 종료
- pkill -f python -> 명령어에 python 포함된 프로세스 종료




