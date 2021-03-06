컴퓨터공학과 20182992 노민규


1. 리눅스 명령어 : top, ps, jobs, kill 명령어 조사하기

top명령어: 
1.시스템의 상태를 전반적으로 가장 빠르게 파악이 가능함(CPU,Memory,Process)
2.옵션없이 입력하면 interval 간격(기본 3초)으로 화면을 갱신하며 정보를 보여줌.
3.디바이스의 성능, 서버의 성능을 체크할 때 유용하며 어떤 프로세스가 CPU를 과다점유하는지 분석도 가능함.

top명령어 실행후 명령어:

shift + p
 CPU 사용률이 높은 프로세스 순서대로 표시

 shift + m
 메모리 사용률이 높은 프로세스 순서대로 표시

 shift + t
 프로세스가 돌아가고 있는 시간 순서대로 표시

 - k
 프로세스  kill  - k 입력 후 종료할 PID 입력 signal을 입력하라고 하면 kill signal인 9를 입력

 - a
 메모리 사용량에 따라 정렬

 - b
 Batch 모드 작동

 - c
 명령행/프로그램 이름 토글

 - d
 지연 시간 간격은 다음과 같다. -d ss. tt (seconds.tenths)

 - h 
 도움말 

 - H
 스레드 토글

 - i
 유휴 프로세스 토글

 - m
 VIRT/USED 토글

 - M
 메모리 유닛 탐지

 - n
 반복 횟수 제한 : -n number

 - p
 PID를 다음과 같이 모니터 : -pN1 -pN2 ... or -pN1, N2 [, ...] 

 - s
 보안 모드 작동

 - S
 누적 시간 모드 토글

 - u
 사용자별 모니터링 : -u somebody

 - U
 사용자별 모니터링 : -U somebody

 - v
 version

 space bar
 refresh

 - u
 입력한 유저의 프로세스만 표시 - which u

 숫자 1
 CPU Core별로 사용량을 보여준다.



-----------------------------------------------------------------------------



ps명령어:
 ps 명령어는 ‘현재’ 실행중인 프로세스 목록과 상태를 보여줌.


ps명령어와 top명령어의 차이점

＊ps는 ps명령어를 입력한 시점의 cpu사용량을 출력
 *top은 일정 주기로 합산해서(실시간) cpu의 사용량을 출력


ps명령어 실행후 명령어:

-A
  모든 프로세스를 출력한다.
  
-a
  세션 리더(일반적으로 로그인 셀)을 제외하고 터미널에 종속되지 않은 모든 프로세스를 출력한다.
  
-e
  커널 프로세스를 제외한 모든 프로세스를  출력해 준다.
  
-f
유닉스 스타일로 출력해주는 옵션으로 UID, PID, PPID등이 함께 표시된다.

-i
 프로세스의 정보를 길게 보여주는 옵션, 우선순위와 관련된 PRI와 NI값을 확인 가능. 
 
-o
출력 포맷을 지정하는 옵션으로 값으로는 pid, tty, time, cmd 등을 지정할 수 있다.

-M
64비트 프로세스들을 보여준다.

-m
프로세스들 뿐만 아니라 커널 스레드들도 보여준다. 

-p
특정 PID를 지정할 때 사용합니다 

-r
현재 실행 중인 프로세서를 보여준다. 

-u
특정 사용자의 프로세스 정보를 확인할 때 사용한다. 사용자를 지정하지 않으면 현재 사용자를 기준으로 정보를 출력한다. 

-x
로그인 상태에 있는 동안 아직 완료되지 않은 프로세서들을 보여준다. 유닉스 시스템은 사용자가 로그아웃 한 후에도 임의의 프로세서가 게속 동작하게 할 수 있다. 그러면 그 프로세서는 자신을 실행시킨 셸이 없이도 계속 자신의 일을 수행하는데 이러한 프로세스는 일반적인 ps 명령으로 확인할 수 잆다. 이 때 -x 옵션을 사용하면 자신의 터미널이 없는 프로세서들을 확인할 수 있다. 

-----------------------------------------------------------------------------

jobs 명령어 (jobs [옵션] [번호] )

jobs 명령어는 작업의 상태를 표시하는 명령어다. 현재 쉘 세션에서 실행시킨 백그라운드 작업의 목록이 출력되며, 각 작업에는 번호가 붙어 있어 kill 명령어 뒤에 '%번호' 등으로 사용할 수 있다.

-l  : 프로세스 그룹 ID를 state 필드 앞에 출력

-n : 프로세스 그룹 중에 대표 프로세스 ID를 출력

-p : 각 프로세스 ID에 대해 한 행씩 출력

command : 지정한 명령어를 실행


jobs로 출력되는 백그라운드 작업의 상태값

Running : 작업이 계속 진항중임

Done : 작업이 완료되어 0을 반환

Done(code) : 작업이 종료되었으며 0이 아닌 코드를 반환

Stopped : 작업이 일시 중단

Stopped(SIGTSTP)  :  SIGTSTP 시그널이 작업을 일시 중단

Stopped(SIGSTOP)  : SIGSTOP 시그널이 작업을 일시 중단

Stopped(SIGTTIN)  :  SIGTTIN  시그널이 작업을 일시 중단

Stopped(SIGTTOU) :  SIGTTOU 시그널이 작업을 일시 중단


-----------------------------------------------------------------------------
kill명령어 (kill [-옵션 or 시그널 ] PID, $kill –9 11)


:프로세스에 특정한 signal을 보내는 명령어이다. 일반적으로 종료되지 않는 프로세스를 종료 시킬 때 많이 사용한다.

옵션

-s 프로세스 종료를 위한 스그널을 지정하는 옵션.(지정되있지 않은 경우 SIGTERM시그널을 사용.

-l 사용 할 수 있는 시그널 및 시그널 번호를 확인하는 명령어.

killall : 프로세스의 이름을 이용해 해당 프로세스를 종료시킴.

시그널/ 시그널번호
1 SIGHUP(HUP) : hang up의 약자로 프로세스를 재시작시키는 시그널이다. 

2 SIGINT(INT) : 인터럽트. 실행을 중지시킨다. [CTRL] + [C] 를 눌렀을 때 보내지는 시그널 이다.

3 SIGQUIT(QUIT) : 키보드 종료 [CTRL] + [\]

4) SIGILL : 잘못된 명령5) SIGTRAP : 트랩 추적
5) 
9 SIGKILL(KILL) : 무조건 종료, 즉 강제 종료시키는 시그널 이다.

15 SIGTERM(TERM) : Terminate의 약자로 가능한 정상 종료시키는 시그널로 kill 명령의 기본

18 CONT : Continue. STOP등에 의해 정지된 프로세스를 다시 실행한다.

19 STOP : 무조건적, 즉각적 정지한다.

20 TSTP : 실행 정지후 다시 실행을 계속하기 위하여 대기시키는 시그널 [CTRL] +[Z] 를 눌렀을 때 보내지는 시그널 이다.


--------------------------------------------------
2.vim 에디터에서 매크로 사용방법에 대하여 조사하기(q , @)

매크로: 같은 동작을 반복하게 해주는 것	

1.q + [name]  
ex) qa :a키에 레코딩을 시작함

2.레코딩을 시작후 매크로의 동작을 입력해줌.

3.반복을 위한 동작의 입력이 끝난후 q를 눌러  레코딩을 종료.

4.등록한 매크로를 실행시키는 방법은 @[name]을 입력.
ex) @a :a키에 등록된 매크로를 실행함. 

[횟수]@[name]으로 매크로를 여러번 실행 할수도있음.
ex)5@a :a매크로를 5번 실행함.

