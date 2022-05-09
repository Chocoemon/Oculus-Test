# 두 번째 VR 실습

https://user-images.githubusercontent.com/68228162/167356174-f1a1efcc-bcd0-4c1a-8a55-43e4cba38c9d.mp4

## 학습 목표: 간단한 볼링 게임을 만들어 XR Origin, Interactor, Interactable의 개념에 대해서 학습하고 활용하도록 한다.

## Pre. 필요한 Unity Package
1. XR Interaction ToolKit

2. OpenXR Plug in
3. 미리 작성된 XRI Defaulut ToolKit - 라이브러리 따로 Import 해줘야함!

## 1. XR Origin 
- 하위 객체로 Camera Offset, Controller 객체들이 여기 속에 들어있음.
- XR Controller 객체에서 HMD와 연결된 컨트롤러의 시그널을 받아옴 

### ※ Tracking Origin Mode
**총 3가지 Properties가 있음**
A. Device: Represents a Device relative tracking origin. A Device relative tracking origin defines a Local Origin at the position of the device in space at some previous point in time, usually at a recenter event, power-on or AR/VR session start. Pose data provided by the device will be in this space relative to the local origin. This means that poses returned in this mode will not include the user height (for VR) or the device height (for AR) and any camera tracking from the XR Device will need to be manually offset accordingly.

B. Floor: Represents the tracking origin whereby** 0,0,0 is on the "floor" **or other surface determined by the XR Device being used. The pose values reported by an XR Device in this mode will include the height of the XR Device above this surface, removing the need to offset the position of the camera tracking the XR Device by the height of the user (VR) or the height of the device above the floor (AR).

C. Unknown:  This indicates that the device does not know, or is unable to determine how it is reporting pose data. This value should be treated as an error condition.

### **※ Action Based Mode 와 Device Based Mode의 차이점** 
Action-based behaviors use Actions to indirectly read input from one or more controls. Device-based behaviors use InputDevice. so you don't need to code for every single possible device. 그니까 다양한 플랫폼을 통합하기 편하다는데, 이는 특정 컨트롤러마다 Set - up을 일일히 해줄 필요가 없으므로 Action Based Mode를 권장하는것. 
![image](https://user-images.githubusercontent.com/68228162/167357134-e6b199d8-6bab-44e4-9280-ef2343f29961.png)

![image](https://user-images.githubusercontent.com/68228162/167357140-aeb396c5-27c8-49a5-ba17-1bdaf3a0b455.png)


## 2. Interactor와 Interatable의 관계
- Interactor는 컨트롤러, 즉 물체와 상호작용하기 위한 어떤 장치
- Interatable은 컨트롤러와 상호작용 가능한 어떠한 물체를 말함 


## Reference 
1. https://mavricresearch.com/2020/11/24/what-you-need-to-know-about-unitys-xr-toolkit-and-its-new-input-system/  (Device based system vs action based system)
