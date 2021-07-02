### Hi there 👋
>#!/usr/bin/env python

import cv2
import numpy as np
import rospkg
import rospy, time
from ackermann_msgs.msg import AckermannDriveStamped
from cv_bridge import CvBridge

bridge = CvBridge()

ack_publisher = None


def img_callback(img_data):
	global bridge
	global cv_image
	cv_image = bridge.imgmsg_to_cv2(img_data, "bgr8")

def drive(steer_val, car_run_speed):
	global ack_publisher
	ack_msg = AckermannDriveStamped()
	ack_msg.drive.steering_angle = steer_val
	ack_msg.drive.speed = car_run_speed
	ack_publisher.publish(ack_msg)

rospy.init_node('video_detect')

ack_publisher = rospy.Publisher('/ackermann_cmd_mux/input/teleop', AckermannDriveStamped, queue_size = 1)

video_path = str(rospkg.RosPack().get_path("lecture_4_ex")) + "/video/1.avi"
capture = cv2.VideoCapture(video_path)
while not rospy.is_shutdown():
	ret, cv_image = capture.read()

	if cv2.waitKey(1) & 0xff == 27:
		break

	if not ret:
		capture.set(CAP_PROP_POS_FRAMES, 1)
		continue

	hsv = cv2.cvtColor(cv_image, cv2.COLOR_BGR2HSV)
	lower_white = np.array([0,0,50])
	upper_white = np.array([179,255,255])
	mask = cv2.inRange(hsv, lower_white, upper_white)
	mask_1 = cv2.cvtColor(mask, cv2.COLOR_GRAY2BGR)
		
	img_canny = cv2.Canny(mask, 50, 150)	
	roi_canny = img_canny[430:450,:]
	# Hough_line = cv2.HoughLines(img_canny, 1, np.pi/180, 100)


	#for i in range(len(Hough_line)):
		#for rho, theta in Hough_line[i]:
			#a = np.cos(theta)
			#b = np.sin(theta)
			#x0 = a*rho
			#y0 = b*rho
			#x1 = int(x0 + 1000*(-b))
			#y1 = int(y0+1000*(a))
			#x2 = int(x0 - 1000*(-b))
			#y2 = int(y0 -1000*(a))
			#cv2.line(cv_image,(x1,y1),(x2,y2),(0,0,255),2)

	left_area_1 = mask[435:445, 0:20]
	left_area_2 = mask[435:445, 5:25]
	left_area_3 = mask[435:445, 10:30]
	left_area_4 = mask[435:445, 15:35]
	left_area_5 = mask[435:445, 20:40]
	left_area_6 = mask[435:445, 25:45]
	left_area_7 = mask[435:445, 30:50]
	left_area_8 = mask[435:445, 35:55]
	left_area_9 = mask[435:445, 40:60]
	left_area_10 = mask[435:445, 45:65]
	left_area_11 = mask[435:445, 50:70]
	left_area_12 = mask[435:445, 55:75]
	left_area_13 = mask[435:445, 60:80]
	left_area_14 = mask[435:445, 65:85]
	left_area_15 = mask[435:445, 70:90]
	left_area_16 = mask[435:445, 75:95]
	left_area_17 = mask[435:445, 80:100]
	left_area_18 = mask[435:445, 85:105]
	left_area_19 = mask[435:445, 90:110]
	left_area_20 = mask[435:445, 95:115]
	left_area_21 = mask[435:445, 100:120]

	right_area_1 = mask[435:445, 550:570]
	right_area_2 = mask[435:445, 570:590]
	right_area_3 = mask[435:445, 590:610]
	right_area_4 = mask[435:445, 610:630]

	stop_area = mask[432:445, 120:520]

	# left area
	if cv2.countNonZero(left_area_21) > 150:
		img_rectangle = cv2.rectangle(cv_image, (100,435), (120,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_21)			

	elif cv2.countNonZero(left_area_20) > 150:
		img_rectangle = cv2.rectangle(cv_image, (95,435), (115,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_20)			

	elif cv2.countNonZero(left_area_19) > 150:
		img_rectangle = cv2.rectangle(cv_image, (90,435), (110,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_19)			

	elif cv2.countNonZero(left_area_18) > 150:
		img_rectangle = cv2.rectangle(cv_image, (85,435), (105,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_18)			

	elif cv2.countNonZero(left_area_17) > 150:
		img_rectangle = cv2.rectangle(cv_image, (80,435), (100,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_17)			

	elif cv2.countNonZero(left_area_16) > 150:
		img_rectangle = cv2.rectangle(cv_image, (75,435), (95,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_16)			

	elif cv2.countNonZero(left_area_15) > 150:
		img_rectangle = cv2.rectangle(cv_image, (70,435), (90,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_15)			

	elif cv2.countNonZero(left_area_14) > 150:
		img_rectangle = cv2.rectangle(cv_image, (65,435), (85,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_14)

	elif cv2.countNonZero(left_area_13) > 150:
		img_rectangle = cv2.rectangle(cv_image, (60,435), (80,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_13)			

	elif cv2.countNonZero(left_area_12) > 150:
		img_rectangle = cv2.rectangle(cv_image, (55,435), (75,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_12)			

	elif cv2.countNonZero(left_area_11) > 150:
		img_rectangle = cv2.rectangle(cv_image, (50,435), (70,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_11)

	elif cv2.countNonZero(left_area_10) > 150:
		img_rectangle = cv2.rectangle(cv_image, (45,435), (65,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_10)

	elif cv2.countNonZero(left_area_9) > 150:
		img_rectangle = cv2.rectangle(cv_image, (40,435), (60,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_9)			

	elif cv2.countNonZero(left_area_8) > 150:
		img_rectangle = cv2.rectangle(cv_image, (35,435), (55,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_8)			

	elif cv2.countNonZero(left_area_7) > 150:
		img_rectangle = cv2.rectangle(cv_image, (30,435), (50,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_7)			

	elif cv2.countNonZero(left_area_6) > 150:
		img_rectangle = cv2.rectangle(cv_image, (25,435), (45,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_6)			

	elif cv2.countNonZero(left_area_5) > 150:
		img_rectangle = cv2.rectangle(cv_image, (20,435), (40,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_5)			

	elif cv2.countNonZero(left_area_4) > 150:
		img_rectangle = cv2.rectangle(cv_image, (15,435), (35,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_4)

	elif cv2.countNonZero(left_area_3) > 150:
		img_rectangle = cv2.rectangle(cv_image, (10,435), (30,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_3)			

	elif cv2.countNonZero(left_area_2) > 150:
		img_rectangle = cv2.rectangle(cv_image, (5,435), (25,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_2)			

	elif cv2.countNonZero(left_area_1) > 150:
		img_rectangle = cv2.rectangle(cv_image, (0,435), (20,445), (0,255,0), 2)
		cnt = cv2.countNonZero(left_area_1)

	# right area
	def right_area():
		if cv2.countNonZero(right_area_1) > 150:
			img_rectangle = cv2.rectangle(cv_image, 
			(550,435), (570,445), (0,255,0), 2)
			cnt = cv2.countNonZero(right_area_1)
			return 0			

		elif cv2.countNonZero(right_area_2) > 150:
			img_rectangle = cv2.rectangle(cv_image, 
			(570,435), (590,445), (0,255,0), 2)
			cnt = cv2.countNonZero(right_area_2)			
			return 1

		elif cv2.countNonZero(right_area_3) > 150:
			img_rectangle = cv2.rectangle(cv_image, 
			(590,435), (610,445), (0,255,0), 2)
			cnt = cv2.countNonZero(right_area_3)			
			return 2

		elif cv2.countNonZero(right_area_4) > 150:
			img_rectangle = cv2.rectangle(cv_image, 
			(610,435), (630,445), (0,255,0), 2)
			cnt = cv2.countNonZero(right_area_4)			
			return 3

	# stop area
	if cv2.countNonZero(stop_area) > 2400:
		img_rectangle = cv2.rectangle(cv_image, (120,432), (520,445), (0,255,0), 2)
		cnt = cv2.countNonZero(stop_area)			
		if cv2.waitKey(1000) > 0:
			break
	print(cnt)

	#res = np.vstack((cv_image_copy,cv_image))
	#cv2.imshow('Hough_line', res)
	cv2.imshow('Lane_detection', img_rectangle[:, :])
	cv2.imshow('Canny_Edge', roi_canny)

	a = right_area()
	if a == 0:
		for right in range(10):
			drive(-0.085, 1)
#			time.sleep(0.1)

	elif a == 1:
		for right in range(10):
			drive(-0.17, 1)
#			time.sleep(0.1)

	elif a == 2:
		for right in range(10):
			drive(-0.255, 1)
#			time.sleep(0.1)

	elif a == 3:
		for right in range(10):
			drive(-0.34, 1)
#			time.sleep(0.1)
	else:	
		for straight_cnt in range(10):
			drive(0,1)
#			time.sleep(0.1)

	if cv2.waitKey(30) > 0:
		break

cap.release()
cv2.destroyAllWindows()

> <launch>
	<include file="/home/nvidia/xycar/src/lecture_4_ex/launch/include/vesc.launch" />
	<node pkg="lecture_4_ex" type="video_detect.py" 
name="video_detect" output="screen" />
</launch>

>https://arclab.tistory.com/164

>https://velog.io/@lolo5329/%EB%85%BC%EB%AC%B8-%EC%9A%94%EC%95%BD-Visualizing-and-Understanding-Convolutional-Networks

>ytrqwe12@gmail.com

>https://public.roboflow.com/object-detection

>개선 방안
- 1 -
YOLOR에 대한 자세한 분석 필요
- 2 -
트럭의 흙에 대한 압력센서 사용에 대한 이해 필요
- 4 -
fps는 최소 20 이상만 나오면 양호, fps에 대한 큰 걱정X
- 3 -
Speed meter 대신 rotary encoder등을 통해 속도 제어
- 4 -
카메라 2개 사용에 대한 processor 속도 저하 고민
- 5 -
배터리 용량에 대한 고민
- 6 -
카메라, Lidar, rotary encoder 3개 동시에 사용하기에 현실적인 문제 고민
- 7 -
공사현장에서는 가상 lane으로 주행 환경 개선

>![Screenshot from 2021-06-25 18-39-59](https://user-images.githubusercontent.com/68285548/123405600-f2efe580-d5e4-11eb-9dde-726e0684a8fc.png)
![Screenshot from 2021-06-25 18-40-02](https://user-images.githubusercontent.com/68285548/123405609-f4211280-d5e4-11eb-9069-419945370393.png)
![Screenshot from 2021-06-25 18-40-28](https://user-images.githubusercontent.com/68285548/123405613-f5523f80-d5e4-11eb-9acf-9628105d1307.png)

>1.  주 1회 1시간정도 내외로 프로젝트 관련 회의 진행(7월은 월요일 8,9월은 주 2회 진행)

2.  전체적인 프로젝트 
	1) 카메라와 Lidar센서를 활용하여 자율주행 차량 구현
	2) Sensor Fusing
	3) CAN 통신 활용

3. H/W
STEP 1.  필요한 부품(자료 조사)
    • USB 카메라 X 3
    • Nvidia Board (Xavier) X 3
    • Lidar X 3
    • RC카 X 3
    • 흰색 테이프
    • 신호등용 LED, 챠량용 LED
    • 부저
    • encoder 모터
    • USB 허브
    • 모터 배터리, 보드용 보조 배터리
    • 모터 드라이버

4. S/W
포장도로에서의 자율 주행
    • 차선 인식
        ◦ OpenCV
        ◦ DeepLearning
        ◦ 혼합
    • 차량, 사람 인식
        ◦ DeepLearning
    • 신호등, 표지판 인식
        ◦ DeepLearning
    • ACC
        ◦ Lidar 사용 
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
