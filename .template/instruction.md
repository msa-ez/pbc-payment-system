## PBC 결제 시스템 개요
PBC 결제 시스템은 모든 결제 관련 작업을 효율적이고 안전하게 처리하도록 설계되었습니다. 이 시스템은 결제 처리, 취소 관리, 거래 내역 조회를 위한 견고한 프레임워크를 제공합니다. 다양한 결제 게이트웨이와의 원활한 통합을 보장하며, 개발자와 최종 사용자 모두에게 사용자 친화적인 인터페이스를 제공합니다.

## 사용 가능한 기능

1) 결제 처리 <br>
  다양한 지원 방법을 통해 사용자가 결제를 할 수 있도록 하며, 안전하고 빠른 거래를 보장합니다.

2) 결제 취소 <br>
   전체 또는 부분 환불 옵션을 통해 결제를 취소할 수 있는 기능을 제공합니다.

3) 거래 내역 조회 <br>
   결제 상태 및 타임스탬프를 포함한 과거 거래의 상세 기록을 사용자가 볼 수 있도록 합니다.

##사용 방법

## 1) 분석/설계
1. Payment System 바운디드 컨텍스트 영역을 더블 클릭하여 PBC 패널을 활성화 합니다.

<img width="1275" alt="image" src="https://github.com/user-attachments/assets/69cebda6-8334-4945-b0b7-7b061ad6c064" /> <br>

2. PBC 패널 옵션중 읽기 요소, 커맨드 요소, 이벤트 요소에서 각각 사용할 기능에 해당하는 이벤트스토밍 스티커를 선택합니다. 

<img width="435" alt="image" src="https://github.com/user-attachments/assets/22365ca1-139f-4582-a95f-bb425bb61383" /> <br>

* 결제를 통한 결제정보 업데이트와 같은 다른 마이크로서비스와의 통신이 발생할 경우
  Event - Policy Relation을 연결해야합니다.

  예시) 결제성공을 통한 주문 애그리거트의 결제정보 변경
  
  <img width="823" alt="image" src="https://github.com/user-attachments/assets/cfaa6b70-a489-42eb-8c18-823b8c9ed7dc" /> <br>
  

## 2) 구현
1. 패널을 닫은 후, CODE를 클릭하여 코드 프리뷰를 통해 이벤트스토밍기반 생성된 코드를 확인합니다.
<img width="714" alt="image" src="https://github.com/user-attachments/assets/4d3f35e7-30cb-483d-a3b5-2fd099101ed4" /> <br>

2. 생성된 코드에서 PaymentSyetem > README.md를 클릭하여 소스코드 사용방법을 확인합니다.
<img width="716" alt="image" src="https://github.com/user-attachments/assets/324887ab-53b3-4bd9-b8ba-823a62bcf764" /> <br>

3. IDE환경에서 소스코드를 Load한 후, README를 참고하여 다운로드 > 압축을 진행하여 소스코드에 payment-system의 코드를 다운로드합니다.
<img width="741" alt="image" src="https://github.com/user-attachments/assets/037b4ac3-dc03-4b96-9d83-dd049629d24f" /> <br>

4. port 충돌을 고려해 application.yml(payment/src/main/resources/application.yml)의 port를 적절하게 변경합니다.
<img width="290" alt="image" src="https://github.com/user-attachments/assets/8809f047-3cc4-4e66-932e-9f89f6f8df5b" /> <br>

5. 이후, EDA기반 통신이 이루어지도록 다른 마이크로서비스와 topic명을 일치 시키기 위해 destination을 수정합니다.
<img width="314" alt="image" src="https://github.com/user-attachments/assets/634d95ea-3d50-43e2-8d95-2a42a51de390" /> <br>

6. Frontend도 동일하게 package.json(frontend/package.json)의 'start'에 명시된 port number를 변경합니다.
<img width="366" alt="image" src="https://github.com/user-attachments/assets/c750e392-c186-4d25-a8a1-2c088a412468" /> <br>

7. 아래 커맨드를 통해 Payment system의 backend, frontend를 기동합니다.
```
// 1. payment Backend

// Root 기준
cd payment-system-0-0-6
cd payment
mvn spring-boot:run

// 2. payment Frontend

// Root 기준
cd frontend
npm install
npm run build
npm run start
```

8. Payment system의 Gateway 라우팅 설정을 진행하기 위해 application.yml(gateway/src/resources/application.yml)에 라우팅을 설정합니다.
<img width="350" alt="image" src="https://github.com/user-attachments/assets/884ee895-b385-43be-aa37-7626b1d70056" /> <br>

9. Root에 위치한 Frontend에 web component 등록을 위해 index.html(frontend/public/index.html)에 Payment system을 아래와 같이 등록합니다.




