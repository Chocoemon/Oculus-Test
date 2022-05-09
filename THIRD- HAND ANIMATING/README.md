# 학습 목표
1. 유니티 환경에서 컨트롤러 및 손의 Rigging 애니메이션을 구현 하는것을 목표로 한다.
2. 각 버튼들의 입력을 받으면 어떻게 Custom한 Method를 일어나게 하는지를 학습힌다. 

## 1. InputDevice 
- Unity는 InputFeatureUsage라고 불리는 C# 구조체를 제공합니다. 이 구조체는 물리 기기 컨트롤(예: 버튼, 트리거)의 표준 집합을 정의하여 
플랫폼의 사용자 입력에 액세스하도록 지원합니다. 이를 통해 이름을 기준으로 입력 타입을 식별할 수 있습니다. 각 InputFeatureUsage의 정의는 
XR.Input.CommonUsages을 참조하십시오.


- 각 InputFeatureUsage는 공통 입력 액션 또는 타입에 해당합니다. 예를 들어 Unity는 사용하는 XR 플랫폼에 관계없이 trigger라고 불리는
InputFeatureUsage를 검지손가락이 제어하는 단일 축 입력으로 정의합니다. InputFeatureUsage를 사용하여 해당 이름으로 trigger 상태를 
가져올 수 있으므로 기존 Unity 입력 시스템에 대해 축(또는 일부 XR 플랫폼의 버튼)을 설정할 필요가 없습니다.

- XR.InputDevices 클래스를 사용하여 현재 XR 시스템과 연결된 입력 기기에 액세스할 수 있습니다. 연결된 모든 기기의 리스트를 가져오려면 
 InputDevices.GetDevices를 사용하십시오.

- 입력 기능에 Access를 가능하게 해주는 함수 ( 버튼이 눌렸는지 안눌렸는지, 조이스틱 축이 돌아가고 있는지 안돌아가고 있는지) 
A. TryGetFeatureValue()
- 특정 기능 값을 검색해서 가져오면 true를 반환합니다.
- 현재 기기가 특정 기능을 지원하지 않거나, 기기가 유효하지 않은 경우(예: 컨트롤러 비활성) false를 반환합니다
- 특정 버튼, 터치 입력 또는 조이스틱 축 값을 가져오려면 CommonUsages 클래스를 사용하십시오. CommonUsages는 포지션, 회전 등과 같은 
- 트래킹 기능을 비롯하여 각 InputFeatureUsage를 XR 입력 매핑 테이블에 포함합니다. 다음 예제 코드는 CommonUsages.triggerButton을 사용하여 
- 사용자가 현재 특정 InputDevice 인스턴스의 트리거 버튼을 누르고 있는지 감지합니다.


`
bool triggerValue;
if (device.TryGetFeatureValue(UnityEngine.XR.CommonUsages.triggerButton, out triggerValue) && triggerValue)
{
    Debug.Log("Trigger button is pressed.");
}
`

B. TryGetFeatureUsages()
 InputDevice.TryGetFeatureUsages 메서드를 사용하여 기기에서 제공하는 전체 InputFeatureUsage 리스트를 가져올 수도 있습니다. 
 이 함수는 기능을 설명하는 타입 및 이름 프로퍼티가 포함된 InputFeatureUsage 항목 리스트를 반환합니다. 다음 예시에는 특정 입력 기기에서 제공된 
 모든 부울 기능이 열거되어 있습니다.
 
 `
 var inputFeatures = new List<UnityEngine.XR.InputFeatureUsage>();
if (device.TryGetFeatureUsages(inputFeatures))
{
    foreach (var feature in inputFeatures)
    {
        if (feature.type == typeof(bool))
        {
            bool featureValue;
            if (device.TryGetFeatureValue(feature.As<bool>(), out featureValue))
            {
                Debug.Log(string.Format("Bool feature {0}'s value is {1}", feature.name, featureValue.ToString()));
            }
        }
    }
}
`

## 2. InputDeviceCharacteristics 
- A set of bit flags describing InputDevice characteristics.
- 그니까, 이 InputDevice가 어떤 타입인지를 알 수 있게 해주는 Bit Flag라고 생각하면 됨!

## Reference 
1. https://docs.unity3d.com/kr/2020.3/Manual/xr_input.html (Input Device 설명) 
