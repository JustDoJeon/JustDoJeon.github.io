---
layout : single
title:  "[JAVA] BufferedReader2"
categories: Dev
tags:
  - [Dev]

toc: true
toc_sticky: true
 
date: '2022-02-09 00:00:00 +0900'

---

> 스타트업 면접을 통해 이 내용에 대한 질문을 받았는데 사용에만 초점을 두고 얕게 공부했더니 대답을 잘 못 한것이 맘에 걸려 다시 포스팅하게 되었다.


![버퍼드리더1](https://user-images.githubusercontent.com/52389219/153218510-709acb75-0674-4291-bc5f-b209d00f5238.PNG)


## BufferedReader를 왜 쓸까 ?

<br>

 - 버퍼를 한번 거쳐가지만 하드디스크의 속도는 느리고 키보드나 모니터와 같은 외부장치와의 데이터 입출력은 생각보다 느리다고한다. 버퍼를 이용해서 데이터를 한데 묶어서 이동하는것이 효율적이고 그냥 전송하게되면 CPU와 성능 갭이 많이 난다고한다.

<BR>

- 공식 문서에 따르면 BufferedReader는 입력 스트림에서 문자를 읽는 함수인데 문자나 배열, 라인들을 효율적으로 읽기 위해서 문자들을 버퍼에 저장하고(버퍼링) 읽는 방법을 취한다고 한다. 

- 버퍼 사이즈도 지정할 수 있지만 기존 디폴트 사이즈가 사용된다.

```JAVA
class BufferedReaderEx {
	public static void main(String[] args) {
		try{
			BufferedReader br  = new BufferedReader(new InputStreamReader(System.in));

			//질문중에 파일을 입력받는다면 어떤걸 사용해야하는지 물어보셨었는데 
			FileReader fr = new FileReader("example.txt");
			//파일의 내용을 갖고 BufferedReader에 넣어서 읽는다.
			BufferedReader br_f = new BufferedReader(fr);

			//BufferedReader를 사용할땐 String으로 반환되기때문에 리턴값이 int 라면 형 변환을 해야한다.
			int num = Integer.parseInt(br.readLine());
			
			br.close(); // 입출력이 끝난후 닫아줌

		}catch (IOException e ){
			e.printStackTrace();
			System.out.print(e.getMessage());
		}
	}
}
```

> InputStreamReader란?

- 우선, 스트림이 뭔지 정리해봤다.

	- 파일데이터 (파일은 그 시작과 끝이 있는 데이터의 스트림이다.)
	- HTTP 응답 데이터(브라우저가 요청하고 서버가 응답하는 HTTP 응답 데이터도 스트림이다.)
	- 키보드 입력 (사용자가 키보드로 입력하는 문자열은 스트림이다.) 
- 입력과 출력을 이어주는것이라고 이해하면 될것같다.

- InputStreamReader(inputStream in) 은 주어진 입력 바이트 스트림 in에 대하여 기본 인코딩을 사용하는 객체를 생성하고 BufferedReader에 그 객체를 넘겨주면서 동작하는것이다.




👉 참조 : [블로그](https://limkydev.tistory.com/50),  [블로그](https://limkydev.tistory.com/66) , [블로그](https://jhnyang.tistory.com/92)

<br>
🌜 개인 공부 기록용 블로그입니다. 오류나 틀린 부분이 있을 경우 
언제든지 댓글 혹은 메일로 지적해주시면 감사하겠습니다! 😄
<br>

**개인메모** 
