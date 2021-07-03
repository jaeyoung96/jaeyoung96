### Hi there 👋

>https://arclab.tistory.com/164

>https://velog.io/@lolo5329/%EB%85%BC%EB%AC%B8-%EC%9A%94%EC%95%BD-Visualizing-and-Understanding-Convolutional-Networks

>ytrqwe12@gmail.com

>https://public.roboflow.com/object-detection

>개선 방안
>- 1 -
>YOLOR에 대한 자세한 분석 필요
>- 2 -
>트럭의 흙에 대한 압력센서 사용에 대한 이해 필요
>- 4 -
>fps는 최소 20 이상만 나오면 양호, fps에 대한 큰 걱정X
>- 3 -
>Speed meter 대신 rotary encoder등을 통해 속도 제어
>- 4 -
>카메라 2개 사용에 대한 processor 속도 저하 고민
>- 5 -
>배터리 용량에 대한 고민
>- 6 -
>카메라, Lidar, rotary encoder 3개 동시에 사용하기에 현실적인 문제 고민
>- 7 -
>공사현장에서는 가상 lane으로 주행 환경 개선

>1.  주 1회 1시간정도 내외로 프로젝트 관련 회의 진행(7월은 월요일 8,9월은 주 2회 진행)
>
>2.  전체적인 프로젝트 
>	1) 카메라와 Lidar센서를 활용하여 자율주행 차량 구현
>	2) Sensor Fusing
>	3) CAN 통신 활용
>
>3. H/W
>STEP 1.  필요한 부품(자료 조사)
>    • USB 카메라 X 3
>    • Nvidia Board (Xavier) X 3
>    • Lidar X 3
>    • RC카 X 3
>    • 흰색 테이프
>    • 신호등용 LED, 챠량용 LED
>    • 부저
>    • encoder 모터
>    • USB 허브
>    • 모터 배터리, 보드용 보조 배터리
>    • 모터 드라이버
>
>4. S/W
>포장도로에서의 자율 주행
>    • 차선 인식
>        ◦ OpenCV
>        ◦ DeepLearning
>        ◦ 혼합
>    • 차량, 사람 인식
>        ◦ DeepLearning
>    • 신호등, 표지판 인식
>        ◦ DeepLearning
>    • ACC
>        ◦ Lidar 사용 

![Screenshot from 2021-06-25 18-39-59](https://user-images.githubusercontent.com/68285548/123405600-f2efe580-d5e4-11eb-9dde-726e0684a8fc.png)
![Screenshot from 2021-06-25 18-40-02](https://user-images.githubusercontent.com/68285548/123405609-f4211280-d5e4-11eb-9069-419945370393.png)
![Screenshot from 2021-06-25 18-40-28](https://user-images.githubusercontent.com/68285548/123405613-f5523f80-d5e4-11eb-9acf-9628105d1307.png)
<!--
**jaeyoung96/jaeyoung96** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:
<a href="https://velog.io/@jae0_bae" target="_blank"><img src="https://img.shields.io/badge/Velog-20c997?style=flat-square&logo=Vimeo&logoColor=white"/></a>
- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
