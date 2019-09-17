#아두이노와 프로세싱을 활용한 시리얼 테스트

20191120 김연빈



[조도 센서 회로만들기]

사진 첨부하려 했으나 사진이 안올려져서 한글파일 첨부 하도록 하겠습니다!!


-[아두이노]

//제 컴퓨터의 포트는 COM3이였습니다!!
//아두이노는 void setup, void loop, 프로세싱은 void setup, void draw 필수!!


void setup(){
 Serial.begin(9600);
 int a;
void loop(){
  a = analogRead(A0);// 아날로그 값을 읽는다
Serial.println(a);
 delay(500);
}

[아두이노 시나리오]

5V 신호선(빨간색)을 조도 센서에 연결
조도센서에 저항연결, 저항에 그라운드(검은색) 연결
조도센서에 A0 신호선(초록색) 연결// 초록색신호선으로 아날로그 값을 읽음  
실행했을 때 손컵으로 덮을 때와 정상 상태의 조도 값이 대체적으로 높을땐 600, 낮을땐 200 제일 높을땐 900으로 나왔습니다
따라서 평균값은 400으로 나왔습니다


[프로세싱]

import processing.serial.*;
Serial p;
void setup(){
size(300,300);// 창크기
p=new Serial(this,"COM3",9600);
}
void draw(){
if(p.available()>0){
String m=p.readString();
int a = int(m.trim());
println(a);
if(a>900) fill(0, 255, 0);//초록
else if(a>400)  fill(255,0,0);//빨강
else fill(0,0,255);//파랑
ellipse(150,150,200,200);
}
}

[프로세싱 시나리오]

값이 400이하면 파랑색 원이 나타나고
값이 900이하이자 400넘으면 빨강색, 이에 응용하여
값이 900이 넘으면 초록색이 나타나도록 프로세싱하였습니다

[작성소감]
어제 수업에서 프로세싱을 처음으로 배우게 됐는데 이해력이 부족하여 혼자하기엔 벅찼습니다 옆에 친구와 머리를 맞대어 교수님의 설명대로 따라가보니 이해가 되었습니다 하지만 제 스스로 부족하다고 생각하여 어제 밤 기숙사에서 1학기때 배운 책을 참고하여 if문에 대하여 더욱 공부하고 복습을 하였습니다 이에  if 문을 사용해 응용까지 할수 있었습니다. 또한 오늘 아침에 일어나서 어제 배웠던 내용들을 다시 코딩해보고 복습하니 완전히 저의 지식으로 습득할수 있었습니다 아두이노도 처음엔 낯설었지만 교수님과 몇주차에 걸쳐 아두이노를 다루다 보니 이젠 익숙해지고 코드를 읽을수 있게 되었습니다 이에 앞으로의 수업도 이해가 안되더라도 교수님의 수업과 함께 어제와 같이 복습하다보면 이해가 될것이란 자신감을 얻을수 있었습니다 앞으로도 교수님을 따라 열심히 하는 김연빈이 되도록 하겠습니다 지켜봐주십시오!! 감사합니다!!  
