# 2025-selection
# Day1
아래는 공지사항 및 처리량 근사치이며 최종값이 아니기 때문에 오류가 있는 경우 변경 될 수 있습니다.
- 과제에 사용하는 파일은 blue, red, green, day1_scheme.sql, blue-hotifx 4개입니다. blue-hotfix는 대회 시작 일정 시간 이후에 전달됩니다.
- 경기 중 채점 요소는 비용, 로드테스트, 카오스이며 경시 시작 한시간 후 부터 스크립트 들이 실행됩니다. 과제 종료 이후에는 해당 작업 및 트레픽들은 발생하지 않습니다.
- EC2는 온디맨드 타입만 사용합니다.
- {등번호}.ws2025.click 호스트존을 생성하고 ns 코드를 전달하면 DNS를 위임 받을 수 있습니다.
- 구성도에 나와 있는것은 Minimal architecture이며 유의사항을 벗어나지 않는 한도내에서 다른 서버스를 이용해도 무방합니다.
  예) NLB를 추가하여 ALB에 고정 IP 제공.
- 채점시 Pod의 네트워크 격리에 대해서는 K8s의 Service에 할당 되는 DNS를 사용합니다. Pod를 바라보는 Service가 생성되어 있어야 하고 해당 Service를 바라보도록 질의도 잘 되어야 합니다.
- RDS는 타입 제한만 있으며 여러대 생성 가능합니다. RDS는 비용 계산에 포함되지 않습니다.
- 14:30까지 별도 DNS 제출이 없으면 http://www.{등번호}.ws2025.click 으로 호출을 시작합니다.
- SQL
  - 타입 2개만 존재 및 phone 57,000 ~ 60,055
    ```
    select type, count(*) as count from device group by type;
    ```
  - before 데이터, 1900 ~ 2005
    ```
    select count(*) from device where type='hotfix' and id like 'before%';
    ```

  # Day2
  - DO NOT manually create Sagemaker AI Model, Endpoints and EndpointConfig. It should be created by ACK.
  - You can use **ml.m6i.xlarge** instead of ml.m5.large, but Elastic inference is not allowed. Only one Notebook instance is allowed. You have to set both the Notebook instance and the Jypyter file name to {your number}-day2.
  - You can choose an instance type of Sagemaker AI Endpoints. There is no stress testing, choose a proper type.
  - You need to implement a bash script and place to `/root/inference.sh` in the bastion host. The script takes the test `.png` file path as a parameter. You will probably need to encode the image file into base64 type before invoking API. It doesn't matter result formatting type, but the class name must be identifiable. Examiners will give 10 test files during the marking.
    ```
    root@localhost# /root/inference.sh 1-class.png
    Airplane
    ```
  - During the marking, entire PyTorch code in the Notebook is re-executed. However, it doesn't trigger to create Sagemaker AI Model, Endpoints and EndpointConfig at the marking time. It means you have to deploy those Sagemaker resources before the end of the competition.
