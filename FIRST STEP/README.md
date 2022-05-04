# pre. XR Tech Stack
![XRTech_Sketch](https://user-images.githubusercontent.com/68228162/166428140-e1b2df90-2b19-48f4-8040-b0e6f06f9dfb.png)


# 1. XR Tool Kit 관련 단어 정리
### A. XR Origin 
- Unity.XR.CoreUtils namespace에 속해있음
- 운동에 의해 조작되는걸 저장해둠.
- 여기에 속해있는 카메라는 Device에서 Rotation과 position 값을 받아와 지속적으로 값을 업데이트함 
- 하위 오브젝트에 있는 컴포넌트 중 Tracked Pose Driver라는 컴포넌트가 있는데, 이는 Device로 부터 위치를 받아와
이 컴포넌트가 속해있는 GameObject의 transform을 변환시켜주는 역할을 함!

### B. XR Interaction Manager
![XR interaction Manager](https://user-images.githubusercontent.com/68228162/166638160-1e917f84-ec31-474d-8372-bf171a4aac44.jpg)

- Interactor와 Interactable이 상호작용하기 위해서는 Interaction Manager가 필요함!
- 기본적으로 Interaction Manager를 생성하지 않는다면, 유니티에서 알아서 생성해줌 
- Ray의 경우, XR Interactor Line visual에서 LineRenderer를 이용해 만들어냄! 색상이 촌스럽거나 패턴, 두께를 조정하고 싶으면 여기에 손을 대면 된다. 

### C. XR Interactor
#### Reference 
1. https://docs.unity3d.com/Manual/XR.html
2. https://www.youtube.com/watch?v=G6EW5YBAjBs (Scene 제작 시 참고)
3. https://docs.unity3d.com/Packages/com.unity.xr.core-utils@2.0/api/Unity.XR.CoreUtils.XROrigin.html
4. https://gongdolhoon.tistory.com/entry/UnityXR-Interaction-Toolkit-VR-2-VR-%EC%84%B8%ED%8C%85%ED%95%98%EA%B8%B0
5. https://docs.unity3d.com/2018.3/Documentation/ScriptReference/SpatialTracking.TrackedPoseDriver.html (Track pose controller)

