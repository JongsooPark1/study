## lotto-step3
---

> 입력한 금액, 자동 생성 숫자, 수동 생성 번호를 입력 기능 추가

### output

```
구입금액을 입력해 주세요.
14000
수동으로 구매할 번호를 입력해 주세요.
8, 21, 23, 41, 42, 43
3, 5, 11, 16, 32, 38
7, 11, 16, 35, 36, 44

수동으로 3장, 자동으로 11개를 구매했습니다.
[8, 21, 23, 41, 42, 43]
[3, 5, 11, 16, 32, 38]
[7, 11, 16, 35, 36, 44]
[1, 8, 11, 31, 41, 42]
[13, 14, 16, 38, 42, 45]
[7, 11, 30, 40, 42, 43]
[2, 13, 22, 32, 38, 45]
[23, 25, 33, 36, 39, 41]
[1, 3, 5, 14, 22, 45]
[5, 9, 38, 41, 43, 44]
[2, 8, 9, 18, 19, 21]
[13, 14, 18, 21, 23, 35]
[17, 21, 29, 37, 42, 45]
[3, 8, 27, 30, 35, 44]

지난 주 당첨 번호를 입력해 주세요.
1, 2, 3, 4, 5, 6
보너스 볼을 입력해 주세요.
7

당첨 통계
---------
3개 일치 (5000원)- 1개
4개 일치 (50000원)- 0개
5개 일치 (1500000원)- 0개
5개 일치, 보너스 볼 일치(30000000원) - 0개
6개 일치 (2000000000원)- 0개
총 수익률은 30%입니다.
```


### analysis

* 메소드 추가

```java
// Input.java
static int getHowManyManual() {
	System.out.println("수동으로 구매할 장수를 입력해주세요");
	String num = sc.nextLine();
	return Integer.parseInt(num);
}

static List<Integer> inputManualLotto() {
	System.out.println("수동으로 구매할 로또 번호를 입력해주세요");
	String inputManualLotto = sc.nextLine();
	String[] splittedManualLotto = inputManualLotto.split(",");
	List<Integer> manualLotto = new ArrayList<>();
	for (String number : splittedManualLotto) {
		manualLotto.add(Integer.parseInt(number));
	}
	return manualLotto;
}
```

* 기존 Lotto 생성 메소드 변경

```java
// Lotto.java
static List<Lotto> createLottos(int howManyManual, int howManyAuto) {
		List<Lotto> lottos = new ArrayList<>();
		for (int i = 0; i < howManyManual; i++) {
			lottos.add(new Lotto(Input.inputManualLotto()));
		}
		for (int i = 0; i < howManyAuto; i++) {
			lottos.add(new Lotto(createLottoNumbers()));
		}
		return lottos;
	}
```
