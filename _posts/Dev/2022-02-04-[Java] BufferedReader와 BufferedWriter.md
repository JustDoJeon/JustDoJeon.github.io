---
layout : single
title:  "[JAVA] BufferedReader와 BufferedWriter "
categories: Dev
tags:
  - [Dev]

toc: true
toc_sticky: true
 
date: '2022-02-04 00:00:00 +0900'

---

> 코딩테스트 학습을 하면서 빠른 입출력 문제를 접했고 BufferedReader와 BufferedWriter에 대한 기본적인 학습을 위해 글을 쓰게되었다.

## BufferedReader의 사용법

<br>

BufferedReader의 많은 메소드들 중 문제를 풀기위해 사용하는 메소드는 두가지다
- readLine()
- close()

먼저, readLine()은 입력값으로 들어온 데이터를 한 줄로 읽어서 **String**으로 바꾸는 메소드다.
무조건 한줄만 읽는다는것을 기억하고 입력값을 받아와야한다.

> ex)
> 5
> 1 2 3 4 5 6 7

이라는 입력값으로 받아야할때, 
숫자 5는 int a = Integer.parseInt(br.readLine()); 으로 바꾸면되지만

<br>
1,2,3,4,5는  요소 하나하나를 가져와야합니다.

```java
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.util.Scanner;
import java.util.StringTokenizer;

public class Solve {

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

		int n = Integer.parseInt(br.readLine());

		StringTokenizer st = new StringTokenizer(br.readLine());
		for (int i = 0; i < n; i++) {
			int a = Integer.parseInt(st.nextToken());
		}
		
		br.close();

	}
}
```

<br>
토큰으로 구분자를 두고 처리한 후에, br.close() 를 통해 자원을 해제하면 됩니다.

## BufferedWriter 사용법

<br>

- BufferedWriter에도 많은 메소드가 있지만 문제 풀이를 위해선 write(), flush(), close() 를 알면됩니다.

- write() : 출력할 내용을 담습니다.
- flush() : 버퍼를 비워내는 동시에 콘솔에 출력하면 됩니다.
- close() : 스트림을 닫습니다.

<br>

```java
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.util.Scanner;
import java.util.StringTokenizer;

public class Solve {

	public static void main(String[] args) throws NumberFormatException, IOException {

		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

		int n = Integer.parseInt(br.readLine());

		for (int i = 0; i < n; i++) {
			StringTokenizer st = new StringTokenizer(br.readLine(), " ");
			int a = Integer.parseInt(st.nextToken());
			int b = Integer.parseInt(st.nextToken());
			bw.write(a + b + "\n");
		}
		bw.flush();
		bw.close();
		br.close();

	}
}
```
- 개행 문자까지 해줘야 정상적으로 답이 출력되었다. 
- a+b는 자동으로  String으로 바뀐다고 한다. 

<br>

👉 참조 : [블로그](https://limkydev.tistory.com/50),  [블로그](https://limkydev.tistory.com/66)

<br>
🌜 개인 공부 기록용 블로그입니다. 오류나 틀린 부분이 있을 경우 
언제든지 댓글 혹은 메일로 지적해주시면 감사하겠습니다! 😄
<br>

**개인메모** 
