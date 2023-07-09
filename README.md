# 자동차 경주 게임
## 진행 방법
* 자동차 경주 게임 요구사항을 파악한다.
* 요구사항에 대한 구현을 완료한 후 자신의 github 아이디에 해당하는 브랜치에 Pull Request(이하 PR)를 통해 코드 리뷰 요청을 한다.
* 코드 리뷰 피드백에 대한 개선 작업을 하고 다시 PUSH한다.
* 모든 피드백을 완료하면 다음 단계를 도전하고 앞의 과정을 반복한다.

## 온라인 코드 리뷰 과정
* [텍스트와 이미지로 살펴보는 온라인 코드 리뷰 과정](https://github.com/next-step/nextstep-docs/tree/master/codereview)

### 기능 목록

1. 자동차 이름을 입력받는 기능
2. 이동할 횟수를 입력받는 기능
3. 자동차가 전진하는 기준을 판단하는 기능
4. 우승 판별 기능
5. 실행 결과를 출력하는 기능

## 객체 설명

### `View`

- `InputView`
  - 자동차 이름과 실행 횟수를 입력받게 하며, 각 입력이 유효한지 검사한다.
  - 유효하지 않은 입력일 경우, 다시 입력받는다.
- `OutputView`
  - 게임 실행 결과를 출력한다.
  - 게임의 우승자를 받아서 우승자를 출력한다.

### `domain`

- `Car`
  - 이름과 위치를 갖는 자동차 객체이다.
  - MOVE_THRESHOLD 이상일 경우 이동한다.
- `CarName`
  - 자동차 이름을 포장하는 객체이다.
- `CarNames`
  - 자동차 이름들을 포장하는 객체이다.
- `CarResponse`
  - 자동차의 정보(이름, 위치)의 정보만을 반환하는 DTO이다.
- `Cars`
  - 자동차 리스트를 관리하는 일급컬렉션이다.
  - `Random` 객체를 생성해 랜덤 값을 생성하고 자동차의 이동 메서드에 전달한다.
- `GameBoard`
  - 자동차 이름들을 입력으로 받아서 자동차 객체를 생성한다.
  - 1회 실행 시 자동차 객체를 이동시킨다. 
  - 게임 종료 후, 우승자 목록을 선정한다.
- `Position`
  - 위치 값을 포장하는 객체
- `TryCount`
  - 실행 횟수를 포장하는 객체

### `Controller`

- `RacingCarController`- 
  - InputView을 활용해서 자동차 이름과 실행 횟수를 입력받는다.
  - 정상적인 입력시, 입력 값에 따라 게임보드 객체를 생성해 게임을 실행한다.
  - OutputView을 활용해서 게임 결과를 출력한다.

### `Main`

- `RacingCarRunner`
  - 메인문