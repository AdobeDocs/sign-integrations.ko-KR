---
title: SugarCRM용 Adobe EchoSign
description: SugarCRM과 Adobe Sign 통합을 활성화하는 설치 안내서
product: Adobe Sign
content-type: reference
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
source-git-commit: 40fe3649aab0499ce8e5fbd1b11308ffbd759a44
workflow-type: tm+mt
source-wordcount: '2354'
ht-degree: 1%

---


# [!DNL SugarCRM]  설치 안내서 {#sugarcrm-install-guide}

[고객 지원 센터에 문의](https://adobe.com/go/adobesign-support-center_kr)

[!DNL SugarCRM]용 Adobe [!DNL EchoSign]은(는) eSignature 및 팩스 서명을 위해 [!DNL SugarCRM]에 전자 서명 자동화를 제공하는 대표적인 eSignature 및 웹 계약 솔루션입니다. 사용자는 SugarCRM에서 계약을 직접 보내고, 계약 내역을 조회하며, 연결된 계정, 연락처, 견적 등과 함께 eSigned 계약을 저장할 수 있습니다.
[!DNL SugarCRM]용 Adobe [!DNL EchoSign]은(는) 온디맨드 또는 온프레미스 솔루션의 경우 6.3 - 6.7을 포함하여 지원되는 모든 버전의 SugarCRM에서 사용할 수 있습니다.

이 문서는 [!DNL SugarCRM] 관리자가 [!DNL SugarCRM] 플러그 인에 대한 Adobe [!DNL EchoSign] 설치 및 구성하는 방법을 학습하는 지침입니다.

## 이 플러그 인 설치 {#install-plugin}

1. [SugarExchange 목록](http://www.sugarexchange.com/product_details.php?product=1123)에서 [!DNL SugarCRM]용 Adobe [!DNL EchoSign]을(를) 가져옵니다.
1. 관리자 계정으로 [!DNL SugarCRM]에 로그인합니다.
1. **[!UICONTROL 관리]** > **[!UICONTROL 모듈 로더]**&#x200B;로 이동합니다.

   ![이미지](images/module-loader.png)

1. [!DNL SugarCRM] 플러그 인에 대한 Adobe [!DNL EchoSign]의 아카이브 파일을 업로드하려면 **[!UICONTROL Browse]**&#x200B;를 선택한 다음 아카이브 파일을 선택한 다음 **[!UICONTROL Upload]**&#x200B;를 선택합니다.
1. 아카이브 파일을 업로드한 후 **[!UICONTROL 설치]**&#x200B;를 선택하여 설치를 시작합니다.
1. 약관을 검토한 다음 **[!UICONTROL Accept]** > **[!UICONTROL Commit]**&#x200B;을 선택합니다.
1. 플러그 인이 성공적으로 설치되면 진행률 표시줄에 100% 성공이 표시됩니다.  진행률 표시줄이 100%에 미치지 못하면 **[!UICONTROL Display Log]**&#x200B;를 선택하여 SugarCRM에서 발생한 오류를 확인합니다.

   ![이미지](images/display-log.png)

1. 설치 후 **[!UICONTROL 관리 > 복구]**&#x200B;로 이동하여 **[!UICONTROL 빠른 복구 및 재구축]**&#x200B;을 선택합니다.

>[!NOTE]
>
>[!DNL SugarCRM] OnDemand에 플러그 인을 설치하는 경우 [!DNL SugarCRM]을(를) 사용하여 지원 티켓을 파일하여 패키지를 설치할 수 있도록 OnDemand에 대한 패키지 검사자의 제한을 일시적으로 제거합니다. 표준 프로세스의 일부입니다.

## 플러그 인 업그레이드 {#upgrade-plugin}

[!DNL SugarCRM] 플러그인에 대한 Adobe [!DNL EchoSign]을 최신 버전으로 업데이트하는 경우 이전 버전을 제거하지 않고 플러그인을 설치해야 합니다.
플러그 인을 업그레이드한 후 **[!UICONTROL 관리]** > **[!UICONTROL 복구]**&#x200B;로 이동한 후 **[!UICONTROL 빠른 복구 및 재구축]**&#x200B;을 선택합니다.

**참고:** 이전 플러그 인을 제거한 경우 제거 중에 테이블을 제거하지 마십시오. 그렇지 않으면 [!DNL EchoSign] 계약 데이터가 손실될 수 있습니다.

## 플러그 인 구성 {#configure-plugin}

1. 이미 Adobe [!DNL EchoSign] 고객인 경우 2단계를 계속합니다.

   [!DNL EchoSign] 계정이 없는 경우 [에서 FREE 14일 평가판](https://sugarcrmintegration.echosign.com/public/login)에 등록하고 온라인 등록 단계에 따라 Adobe [!DNL EchoSign] 계정을 사용할 수 있습니다.
1. [Echo Sign 계정](http://www.echosign.com)에 로그인하고 다음 단계를 수행하십시오.
   1. **[!UICONTROL 계정]** 탭을 선택합니다.
   1. 왼쪽 아래에서 **[!UICONTROL EchoSign API]**&#x200B;를 선택합니다.
   1. **[!UICONTROL API 액세스 활성화]**&#x200B;를 선택하고 페이지에서 API 키를 가져옵니다.

   ![이미지](images/enable-api-access.png)

1. SugarCRM에서 **[!UICONTROL Administration]** > **[!UICONTROL Adobe EchoSign Settings]**&#x200B;로 이동하여 **[!UICONTROL EchoSign API Key]**&#x200B;라는 필드에 API 키를 입력합니다.
1. 선택적으로 다음 설정으로 플러그 인을 구성합니다.

   1. 견적에서 계약을 작성할 때 PDF 자동 첨부: [!DNL SugarCRM] 사용자가 Quotes 모듈에서 EchoSign 계약을 작성하는 경우 견적의 PDF를 자동으로 첨부할지 여부를 선택합니다.
   1. 받는 사람 목록 관리: [!DNL EchoSign] 계약 모듈의 받는 사람 하위 패널에 표시할 모듈을 선택합니다. 또한 [!DNL EchoSign] 계약 하위 패널이 해당 모듈에 추가됩니다.
   1. 다음 모듈에 보내기 단추 추가: Create [!DNL EchoSign] Agreement 버튼/액션을 Quote 모듈의 기본 액션에 포함시키려면 선택합니다.
   1. 설정을 저장하려면 **[!UICONTROL 저장]**&#x200B;을 선택합니다.

**참고:** Adobe  [!DNL EchoSign] for 플러그인 [!DNL SugarCRM] 에는  [PHP SOAP 확장이 필요합니다](http://www.php.net/manual/en/book.soap.php). SOAP 지원을 사용하려면 enable-soap을 사용하여 PHP를 구성합니다.

## 계약 업데이트 가져오기(버전 6.3 이상 [!DNL SugarCRM]) {#get-agreement-updates}

버전 6.3 이상의 경우 다음 두 가지 옵션을 사용하여 계약 업데이트를 가져올 수 있습니다. 이전 버전의 SugarCRM에서는 기본적으로 플러그 인은 콜백 메서드(옵션 1)만 제공합니다.

### 옵션 1: 업데이트를 EchoSign으로 푸시하기 위한 콜백 메서드 설정

웹 사이트가 공용 페이지이면 새 이벤트가 발생할 때마다 Adobe EchoSign에서 [!DNL SugarCRM] 인스턴스에 ping을 수행할 수 있습니다. [!DNL SugarCRM] 그런 다음 계약 상태, 이벤트를 업데이트하고 서명된 문서(서명된 경우)를 자동으로 및 실시간으로 다운로드합니다. 방화벽 뒤에 있는 경우에는 [!DNL EchoSign] 서버 IP 주소를 화이트리하거나 이 안내서의 다음 섹션에 설명된 EchoSign 계약을 업데이트하는 예약된 작업 방법을 사용해야 합니다.

1. **[!UICONTROL 관리]** > **[!UICONTROL Adobe EchoSign 설정]**&#x200B;으로 이동합니다.
1. **[!UICONTROL EchoSign 콜백 메서드]** 확인란을 선택하여 계약의 이벤트 및 상태를 업데이트합니다.
1. **[!UICONTROL Save]**&#x200B;를 선택합니다.

### 옵션 2: 방화벽 뒤에 있는 [!DNL SugarCRM] 인스턴스에 대해 예약된 작업 설정

[!DNL SugarCRM] 플러그 인의 [!DNL EchoSign]은(는) 예약된 작업을 사용하여 서명을 위해 종료되는 계약에 대한 업데이트를 [!DNL EchoSign]에 쿼리할 수도 있습니다. 온-프레미스 [!DNL SugarCRM] 설치가 방화벽 뒤에 있는 경우 예약된 작업 쿼리 방법을 사용할 수 있습니다.

설정하려면

1. **[!UICONTROL 관리]** > **[!UICONTROL 스케줄러]**&#x200B;로 이동합니다.
1. 탭 드롭다운 메뉴에서 **[!UICONTROL 스케줄러 만들기]**&#x200B;를 선택합니다.
1. 작업 이름을 입력합니다.
1. 작업 필드에서 **[!UICONTROL Adobe EchoSign Status Updater]**&#x200B;를 선택합니다.
1. 필요에 따라 자주 실행되도록 작업을 설정합니다. 10분마다 실행되도록 설정하는 것이 좋습니다. 즉, 계약을 열거나 읽거나 서명한 후 [!DNL SugarCRM]이(가) 해당 정보로 업데이트되는 데 최대 10분이 걸릴 수 있습니다.

   **참고:** 서명을 위해 많은 계약이 있는 경우 이 작업을 너무 자주 실행하면 시스템 속도가 느려질 수 있습니다.

   ![이미지](images/echosign-status-updater.png)

1. **[!UICONTROL 관리]** > **[!UICONTROL Adobe EchoSign 설정]**&#x200B;으로 이동합니다.
1. **[!UICONTROL EchoSign 콜백 메서드 사용]** 상자의 선택을 취소하여 계약의 이벤트 및 상태를 업데이트합니다.
1. **[!UICONTROL Save]**를 선택합니다.
참고: 이 작업을 수행하려면 [!DNL SugarCRM]에서 스케줄러를 켭니다.

다른 [!DNL SugarCRM] 모듈에 EchoSign 계약을 추가하려면 다음과 같이 하십시오.

1. **[!UICONTROL 관리]** > **[!UICONTROL Studio]**&#x200B;로 이동합니다.
1. 왼쪽 열 폴더 트리에서 [!DNL EchoSign] 계약을 추가할 모듈을 선택합니다.
1. **[!UICONTROL 관계]** **[!UICONTROL 관계 추가]**&#x200B;를 선택합니다.
1. 드롭다운 메뉴에서 Type as **[!UICONTROL One to Many]**&#x200B;를 선택하고 Module as **[!UICONTROL EchoSign Agreements]**&#x200B;를 선택합니다.
1. **[!UICONTROL 저장 및 배포]**&#x200B;를 선택합니다.

   ![이미지](images/save-and-deploy.png)

   [!DNL EchoSign] 이제 계약이 모듈에 표시되고 계약을 생성하여 추적할 수 있습니다.

   ![이미지](images/echosign-agreements.png)

**기타 구성 단계**

* **모듈  [!DNL EchoSign] 숨기기**: 관리&quot;  [!DNL EchoSign] 표시 모듈 탭 및 하위  [!DNL EchoSign] 패널로 이동하여 숨겨진 열로 이동하여 받는 사람 및 이벤트 모듈을 숨길 수 있습니다.
* **packageScan을 사용하지 않도록 설정하는 중**: 자체 시스템에서 packageScan을 사용하도록 설정한 경우 설치 중에 비활성화해야 합니다. [!DNL SugarCRM] 온디맨드(on-Demand)를 사용하는 경우 [!DNL SugarCRM] 지원에 문의하여 packageScan을 사용하지 않도록 설정하십시오.

## 플러그 인 제거 {#uninstall-plugin}

1. 관리자 계정으로 [!DNL SugarCRM]에 로그인합니다.
1. **[!UICONTROL 관리]** > **[!UICONTROL 모듈 로더]**&#x200B;로 이동합니다.
1. **[!UICONTROL SugarCRM용 EchoSign 플러그인] 옆에 있는 [!UICONTROL Uninstall]**&#x200B;을 선택합니다.
1. 제거를 시작하려면 **[!UICONTROL 커밋]**&#x200B;을 선택하십시오. 플러그인에 대해 생성된 데이터베이스 테이블을 제거하도록 선택할 수도 있습니다.

   ![이미지](images/uninstall-plugin.png)

   플러그 인이 성공적으로 제거되면 진행률 표시줄에 100% 성공이 표시됩니다. 진행률 표시줄이 100%에 미치지 못하면 [!UICONTROL Display Log]를 선택하여 SugarCRM에서 발생한 오류를 확인합니다.

   ![이미지](images/uninstall-display-log.png)

## [!DNL SugarCRM]에 Adobe [!DNL EchoSign] 사용 {#use-echosign-for-sugarcrm}

계정, 연락처, 견적 또는 기타 [!DNL SugarCRM] 모듈과 연결된 Adobe [!DNL EchoSign] 계약을 만들 수 있습니다. 파일을 첨부하고, 수신자를 지정하고, 서명을 위해 보낼 수 있습니다. Adobe [!DNL EchoSign]는 계약의 현재 상태로 [!DNL SugarCRM]을(를) 업데이트하고 계약이 완전히 실행되면 [!DNL SugarCRM]에 서명된 계약을 저장합니다.

### Adobe [!DNL EchoSign] 계약 만들기 및 편집 {#create-edit-agreements}

[!DNL EchoSign] 계약 모듈 또는 [!DNL SugarCRM] 관리자가 구성한 모듈을 통해 계약을 생성할 수 있습니다.

1. [!UICONTROL EchoSign Agreements] 탭의 [!UICONTROL Actions] 목록에서 **[!UICONTROL Create EchoSign Agreement]**&#x200B;를 선택합니다.
1. [!DNL EchoSign] 계약의 기본 섹션에서 다음 정보를 입력하거나 다양한 계약 옵션 중에서 선택합니다.

   1. **[!UICONTROL 이름:]** 계약의 이름을 입력합니다.
   1. **[!UICONTROL 서명 유형:]** 문서에 허용되는 서명 유형을 선택합니다. 전자 서명 및 팩스 서명이 옵션으로 제공됩니다.
   1. **[!UICONTROL 또한 이 계약에 서명해야 합니다. 보낸 사람이 계약에 서명해야 하는지 여부를]** 나타냅니다.
   1. **[!UICONTROL 서명 순서:이 계약에 서명해야 함 이전 옵션이 선택된]** 경우 보낸 사람과 받는 사람이 서명해야 하는 순서도 선택합니다.
   1. **[!UICONTROL 받는 사람에게 서명하도록 알림:받는 사람에게 문서에 서명하도록 메시지를]** 표시하는 빈도를 선택합니다. 매일 또는 매주 옵션이 있습니다.
   1. **[!UICONTROL 서명 기한(일):]** 계약이 서명되어야 할 날짜를 지정합니다.
   1. **[!UICONTROL 미리 보기, 서명 또는 양식 필드 추가:계약이 전송되기 전에 미리 보기를 선택하거나 서명 필드, 초기 필드 또는 기타 양식 필드를 계약자에게 보내기 전에 계약에 끌어 놓으려면 이 옵션을]**  선택합니다. 문서를 미리 보거나 원하는 필드를 문서로 드래그한 후 [보내기] 단추를 선택하여 계약을 받는 사람에게 보냅니다.
   1. **[!UICONTROL 첫 번째 서명자에 대한 호스트 서명:보낸 사람이 직접 계약 서명을 호스팅할 것인지 여부를]** 나타냅니다.
      * **[!UICONTROL 메시지:]** 받는 사람에 대한 메시지를 포함합니다.
      * **[!UICONTROL 계정, 기회, 견적:이 계약과 연관된 계정, 기회 또는 견적을]** 선택하거나 수정합니다.
      * **[!UICONTROL 언어:받는 사람에게 서명 페이지 및 전자 메일 알림이 표시되는 언어를]** 지정합니다.

      ![이미지](images/create-agreements.png)


1. [!UICONTROL EchoSign 계약]의 [!UICONTROL 보안 옵션] 섹션에서 다음 정보를 입력합니다.

   a) **[!UICONTROL 서명에 필요한 암호:]** 받는 사람이 문서에 서명하기 전에 암호를 입력해야 하는지 여부를 나타냅니다.
b) **[!UICONTROL 열기 필수 암호:]** 수신자가 계약 또는 서명된 계약의 PDF를 열기 전에 암호를 입력해야 하는지 여부를 나타냅니다.
c) **[!UICONTROL 암호:]** 서명하거나 문서를 여는 데 사용할 암호를 지정합니다.
d) **[!UICONTROL 암호 확인:]** 서명하거나 문서를 여는 데 사용할 암호를 확인합니다.

1. [!DNL EchoSign] 계약의 기타 섹션에서 다음 정보를 입력합니다.

   a) **[!UICONTROL 사용자:]** [!DNL SugarCRM] 사용자를 지정하십시오. 기본값은 현재 시스템에 로그인한 사용자입니다.
b) **[!UICONTROL Teams:]** 기본 팀 할당을 변경하려면 새 기본 팀 이름을 입력합니다. 레코드에 추가 팀을 할당하려면 **[!UICONTROL 선택]**&#x200B;을 클릭하고 팀 목록에서 팀을 선택하거나 **[!UICONTROL 추가를 선택하여 팀 필드를 추가하고 팀 이름을 입력합니다.]** 자세한 내용은 [!DNL SugarCRM] Application Guide의 &#39;Assigning Records to Users and Teams&#39;를 참조하십시오.

1. **[!UICONTROL Save]**&#x200B;를 선택합니다.

### [!DNL EchoSign] 계약 세부 정보 보기 {#agreement-detail-view}

[!DNL EchoSign] 계약이 저장된 후 계약의 세부 정보 보기에는 다음 하위 패널이 포함됩니다.

* **[!UICONTROL 수신자:]** 이 하위 패널에 나열된 모든 연락처는 문서 하위 패널에 지정된 문서를 받습니다. 계약을 보내기 전에 받는 사람을 하나 이상 추가해야 합니다.
* **[!UICONTROL 문서:]** 새 문서를 업로드하거나 서명을 위해 보낼 문서 [!DNL SugarCRM] 를 선택합니다.
* **[!UICONTROL 이벤트:]** 계약이 서명을 위해 전송되거나, 보거나, 서명되는 경우와 같은 계약과 관련된 모든 작업이 이 하위 패널에 나열됩니다.
[!DNL EchoSign] 계약을 편집하려면 계약의 [!UICONTROL 세부 정보 보기]에서 [!UICONTROL 편집] 단추를 선택하십시오.

![이미지](images/agreement-detail-view.png)

**참고:** 서명을 위해 계약을 보낸 후 세부 정보 보기에서   편집 단추가 제거되어 이벤트 레코드를 유지합니다. 그러나 편집 단추를 활성화할 수 있습니다. 이렇게 하려면 [!UICONTROL Admin] > [!UICONTROL Adobe EchoSign Settings] 옵션의 선택을 취소하십시오. 서명을 위해 계약이 전송된 후 *[!UICONTROL 를 편집하거나 삭제할 수 없게 하십시오.]*

### [!DNL EchoSign] 계약에 문서 추가 {#add-document}

[!DNL SugarCRM] 사용자는 EchoSign 계약 레코드의 Documents 하위 패널을 사용하여 새 문서를 업로드하거나 이미 에 업로드된 문서 [!DNL SugarCRM] 를 선택할 수 있습니다.
문서를 업로드하려면 [!UICONTROL Documents] 하위 패널에서 **[!UICONTROL Upload Document]**&#x200B;를 선택합니다.

해당 양식의 개별 필드에 대한 자세한 내용은 [!DNL SugarCRM] Application Guide의 &#39;Documents Module&#39; 섹션을 참조하십시오.

문서를 선택하려면 문서 하위 패널에서 **[!UICONTROL 선택]**&#x200B;을 클릭합니다. 하위 패널에서 관련 정보를 관리하는 방법에 대한 자세한 내용은 [!DNL SugarCRM] Application Guide의 &#39;Viewing and Managing Record Information&#39;을 참조하십시오.

![이미지](images/add-document-to-agreement.png)

### [!DNL EchoSign] 계약에 대한 받는 사람 지정 {#specify-recipient}

1. [!UICONTROL 계약의 [!DNL EchoSign]받는 사람] 하위 패널에서 **[!UICONTROL 받는 사람 추가]**&#x200B;를 선택합니다.
1. 다음 정보를 입력합니다.
a) [!UICONTROL 받는 사람:] 드롭다운 메뉴에서 받는 사람 유형을 선택합니다. 텍스트 필드에 받는 사람의 이름이나 전자 메일 주소를 입력합니다. [!DNL SugarCRM] 입력할 때 이름을 찾아 선택 목록을 제공합니다. 일치하는 항목이 있으면 이름을 선택합니다. 화살표 아이콘을 선택하여 팝업 창에서 이름을 선택할 수도 있습니다. 필드에서 이름을 지우려면 **[!UICONTROL X]** 아이콘을 선택합니다.
b) [!UICONTROL 역할:] 드롭다운 메뉴에서 역할을 선택합니다. 서명자 및 참조 및 승인자가 옵션으로 제공됩니다. 승인자는 문서에 서명할 필요가 없습니다.
1. 저장을 선택합니다.

![이미지](images/add-recipient-to-agreement.png)

### 서명에 대한 계약 보내기 {#send-for-signature}

서명을 위해 계약을 보낼 준비가 되면 페이지 왼쪽 상단의 드롭다운 메뉴에서 **[!UICONTROL 서명을 위해 보내기]**를 선택합니다. 수신자는 서명을 기다리는 문서를 알려주는 이메일을 받는다. 받는 사람이 문서에 서명하면 보낸 사람은 전자 메일 알림을 받습니다.
[!UICONTROL 첫 번째 서명자를 위한 호스트 서명] 옵션이 선택된 경우 **[!UICONTROL 서명을 위한 보내기]**&#x200B;를 선택하여 서명자가 보낸 사람과 함께 문서에 서명할 수 있습니다.

![이미지](images/send-for-signature.png)

**[!UICONTROL 현재 서명자를 위한 호스트 서명]** 링크는 문서가 서명될 때까지 액세스할 수 있는 [!UICONTROL 첫 번째 서명자를 위한 호스트 서명] 필드 옆에도 나타납니다. 이 링크를 사용하여 여러 서명자에 대한 계약 서명을 호스팅하거나 실수로 닫은 경우 팝업 창을 다시 열 수 있습니다.
[!UICONTROL 미리 보기, 서명 위치 지정 또는 양식 필드 추가] 옵션이 선택된 경우 보낸 사람이 문서를 미리 보거나 문서를 보내기 전에 문서로 필드를 끌어 오도록 하려면 **[!UICONTROL 서명을 보내기]**&#x200B;를 선택합니다. 계약을 받는 사람에게 보내려면 해당 창에서 **[!UICONTROL 보내기]**&#x200B;를 선택해야 합니다.

그림 5: 서명을 위해 문서를 수신자에게 보내려면 서명을 위해 보내기를 선택합니다.

### 견적 레코드에서 보내기 {#send-from-quote-record}

Adobe [!DNL EchoSign]은(는) [!DNL SugarCRM]에서 Quotes와 직접 통합되므로 견적의 PDF가 자동으로 생성되어 계약 레코드에 첨부됩니다.
견적을 볼 때 **[!UICONTROL Create EchoSign Agreement]**&#x200B;를 선택하여 견적을 생성하고 계약에 자동으로 첨부합니다. 또한 새로운 계약은 관련 Opportunity, Account 또는 Quote 를 자동으로 연관시킵니다.

![이미지](images/create-echosign-agreement.png)

계약에 대한 견적 PDF의 자동 첨부를 해제하려면 **[!UICONTROL 관리]** > **[!UICONTROL Adobe EchoSign 설정]**&#x200B;으로 이동하고 *[!UICONTROL Quote]*&#x200B;에서 계약을 만들 때 PDF 자동 첨부 상자의 선택을 취소하십시오.

### 계약 취소 {#cancel-agreement}

모든 수신자가 아직 문서에 서명하지 않은 경우 서명을 위해 보낸 후 [!DNL EchoSign] 계약을 취소할 수 있습니다. 서명을 위해 문서를 보낸 후 계약의 세부 정보 보기에 [!UICONTROL 계약 취소] 단추가 나타납니다. 계약을 취소하려면 **[!UICONTROL 계약 취소]**&#x200B;를 선택합니다.

![이미지](images/cancel-agreement.png)

참고: 서명을 위해 [!DNL EchoSign] 계약이 전송되고 레코드가 삭제되면 계약을 삭제하기 전에 계약을 취소해야 합니다.

### 서명 추적 {#track-signatures}

[!UICONTROL 계약의 ] 하위 패널은 서명을 위해 전송된 계약의 상태를 추적합니다. [!DNL EchoSign] [!DNL EchoSign] 계약의 최신 업데이트를 보려면 **[!UICONTROL 상태 업데이트]**&#x200B;를 선택하십시오. [!UICONTROL 상태 업데이트] 단추는 서명을 위해 계약을 보낸 후에만 사용할 수 있습니다.

![이미지](images/update-cancel-status.png)

서명에 대한 계약을 보낸 후 **[!UICONTROL 업데이트 상태]**&#x200B;를 선택하여 최신 상태를 검색합니다.

![이미지](images/events-subpanel.png)

### 미리 알림 보내기 {#send-reminders}

계약을 보낸 후 현재 서명자에게 미리 알림을 보내려면 **[!UICONTROL 미리 알림 보내기]**&#x200B;를 선택합니다. 서명을 기다리는 계약에 대한 전자 메일 미리 알림을 현재 서명자에게 즉시 보냅니다.

![이미지](images/send-reminder.png)
