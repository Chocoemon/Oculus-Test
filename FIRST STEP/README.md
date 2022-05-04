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
- 여기서 Interactor는 컨트롤러를, Interactable은 상호작용을 받는 물체를 의미함
- Interactor는 Select, hover, grab 총 3개의 동작이 가능하다. 
- Interactor는 Direct, Ray, Socket 총 3종류가 있다.
- Interactable은 Grab이 있다. (Simple interactable은 뭐지?)
- 기본적으로 Interaction Manager를 생성하지 않는다면, 유니티에서 알아서 생성해줌 
- Ray의 경우, XR Interactor Line visual에서 LineRenderer를 이용해 만들어냄! 색상이 촌스럽거나 패턴, 두께를 조정하고 싶으면 여기에 손을 대면 된다. 
- Interactable은 Collider나 Raycaster에 의해 탐지가 가능하다. 


### C. XR Ray Interactor
- 각 HandController에 붙어 있는 컴포넌트 중 하나 
-  Interactor used for interacting with interactables at a distance. This is handled via ray casts
-  RayCast가 포물선으로 나가게 할건지, 베지어 곡선에 따라서 나가게 할 건지, 직선으로 나가게 할 건지를 메뉴에서 선택이 가능하다. 

### D. XR Grab Interactable
- Interactable component that allows basic "grab" functionality.
-  Can attach to a selecting Interactor and follow it around while obeying physics (and inherit velocity when released).

### E. XR Direct Interactable

#### Reference 
1. https://docs.unity3d.com/Manual/XR.html
2. https://www.youtube.com/watch?v=G6EW5YBAjBs (Scene 제작 시 참고)
3. https://docs.unity3d.com/Packages/com.unity.xr.core-utils@2.0/api/Unity.XR.CoreUtils.XROrigin.html
4. https://gongdolhoon.tistory.com/entry/UnityXR-Interaction-Toolkit-VR-2-VR-%EC%84%B8%ED%8C%85%ED%95%98%EA%B8%B0
5. https://docs.unity3d.com/2018.3/Documentation/ScriptReference/SpatialTracking.TrackedPoseDriver.html (Track pose controller)
6. https://learn.unity.com/tutorial/using-interactors-and-interactables-with-the-xr-interaction-toolkit# (Interactor toolkit tutorial)
7. https://sneakydaggergames.medium.com/how-to-create-a-vr-instance-in-unity-set-up-vr-bowling-5ab4e631e00a

