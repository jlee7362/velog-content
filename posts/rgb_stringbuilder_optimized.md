---
title: 자바로 RGB 색 조합 출력하기 - StringBuilder로 성능 개선하기
tags: [Java, StringBuilder, 입출력 최적화, RGB 조합]
description: 자바에서 반복문을 이용한 RGB 조합 출력 예제와 함께, 출력 성능을 향상시키는 StringBuilder 사용 방법을 소개합니다.
date: 2025-04-11
---

# 🎨 자바로 RGB 색 조합 출력하기  
RGB 조합을 출력하는 간단한 자바 코드를 만들고, 출력 속도와 메모리 최적화를 위해 `StringBuilder`를 활용해 개선해봅니다.

---

## 📌 기본 목표  
- 입력된 r, g, b 값으로 가능한 RGB 조합 출력
- 조합 수 세기
- 성능 개선 전/후 비교

---

## 🧑‍💻 기본 코드 (출력 성능 이슈 있음)

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int i, j, k, c=0;
        int r, g, b;
        String[] input = sc.nextLine().split(" ");
        r = Integer.parseInt(input[0]);
        g = Integer.parseInt(input[1]);
        b = Integer.parseInt(input[2]);

        for (i = 0; i < r; i++) {
            for (j = 0; j < g; j++) {
                for (k = 0; k < b; k++) {
                    System.out.print(i + " ");
                    System.out.print(j + " ");
                    System.out.println(k + " ");
                    c++;
                }
            }
        }
        System.out.printf("%d", c);
        sc.close();
    }
}
```

---

## 🧪 문제점 분석

- `System.out.print`/`println`를 **매 반복마다 호출** → 느림
- 출력 횟수가 많아지면 **시간 + 메모리 증가**

예) `r=100, g=100, b=100` 이면  
→ 출력 100만 줄, I/O 연산 약 300만 회

---

## 🚀 개선된 코드: `StringBuilder` 사용

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int i, j, k, c = 0;
        int r, g, b;
        String[] input = sc.nextLine().split(" ");
        r = Integer.parseInt(input[0]);
        g = Integer.parseInt(input[1]);
        b = Integer.parseInt(input[2]);

        StringBuilder sb = new StringBuilder();

        for (i = 0; i < r; i++) {
            for (j = 0; j < g; j++) {
                for (k = 0; k < b; k++) {
                    sb.append(i).append(" ")
                      .append(j).append(" ")
                      .append(k).append("\n");
                    c++;
                }
            }
        }

        System.out.print(sb.toString());
        System.out.printf("%d", c);
        sc.close();
    }
}
```

---

## ✅ 결과 비교

| 항목             | 기본 코드       | 개선 코드 (StringBuilder) |
|------------------|----------------|----------------------------|
| 메모리 사용량    | 약 196180KB    | ↓ 20~30% 감소 예상         |
| 실행 시간        | 약 2970ms      | ↓ 2~3배 빨라짐             |
| 출력 함수 호출수 | 약 3,000,000회 | 1회                        |

---

## 📎 마무리

- `StringBuilder`는 많은 문자열을 출력할 때 필수 도구
- 반복 출력은 가능하면 한 번에 모아서 출력하자
- 자바의 입출력 성능은 생각보다 큰 차이를 만든다

---

## 🔜 다음 주제
- `BufferedWriter`로 더 강력한 출력 최적화
- RGB 조합을 파일로 저장하는 방법
