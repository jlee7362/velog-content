---
title: valueOf로 16진수 입력받아 구구단 출력하기
tags: [Java, valueOf, Scanner]
description: 자바에서 입력값을 16진수로 받고, 구구단을 출력해보자.
date: 2025-04-11
---

# 🚀 valueOf로 16진수 입력받아 구구단 출력하기  
자바에서 `valueOf` 기능을 활용한 예제. 핵심은 `valueOf`를 통해 입력 문자열을 16진수로 해석하여 구구단을 출력하는 것이다.

---

## 📌 목표  
- 사용자 입력을 16진수로 해석
- `Integer.valueOf()` 메서드 활용
- 16진수 출력 포맷 학습

---

## 🧑‍💻 전체 코드

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String a = sc.nextLine();
        int number = Integer.valueOf(a, 16);

        for (int i = 1; i < 16; i++) {
            System.out.printf("%X*%X=%X\n", number, i, (number * i));
        }
    }
}
```

---

## ✍️ 코드 설명  

- `Scanner sc = new Scanner(System.in);`  
  → 사용자 입력을 받기 위한 표준 방식

- `Integer.valueOf(a, 16);`  
  → 문자열을 16진수로 해석하여 정수로 변환

- `System.out.printf("%X", num);`  
  → 정수를 16진수 대문자로 출력

---

## 🧪 실행 예시  

**입력 예시**  
```
A
```

**출력 예시**  
```
A*1=A  
A*2=14  
A*3=1E  
...
```

---

## ✅ 정리  

- `Integer.valueOf(s, 진수)` → 문자열 진법 처리 가능  
- `printf("%X")` → 16진수 포맷 출력  
- `Scanner`로 입력 받아 `int`로 변환하면 다양한 계산에 활용 가능

---

## 📎 참고 / 다음 주제  

- `parseInt()` vs `valueOf()` 차이  
- 다음에는 2진수 출력도 해보기  
