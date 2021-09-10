---
title: Workday 설치 안내서
description: Adobe Sign과 Workday 통합을 활성화시키기 위한 설치 안내서
uuid: 56478222-fe66-4fa5-aac3-0ecdf2863197
product: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
discoiquuid: 29d55a25-6e2f-4c59-ae7c-c21bb82cecba
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 8f12b524-2123-45d4-98d5-b2b23580a5ea
source-git-commit: d462ccf41fa5483cfa02f5eaf154c23f26157a1e
workflow-type: tm+mt
source-wordcount: '1137'
ht-degree: 19%

---

# [!DNL Workday] 설치 안내서{#workday-installation-guide}

[**Adobe Sign 지원 문의**](https://adobe.com/go/adobesign-support-center_kr)

## 개요 {#overview}

이 문서에서는 Adobe Sign을 [!DNL Workday] 테넌트에 통합하는 방법에 대해 설명합니다. [!DNL Workday] 내에서 Adobe Sign을 사용하려면 다음과 같은 [!DNL Workday] 항목을 만들고 수정하는 방법을 알아야 합니다.

* 비즈니스 프로세스 프레임워크
* 테넌트 설정 및 구성
* 보고 및 [!DNL Workday] Studio 통합

통합을 완료하는 상위 단계는 다음과 같습니다.

* Adobe Sign에서 관리 계정 활성화(신규 고객만 해당)
* [!DNL Workday] 통합 사용자를 보유할 그룹 구성
* [!DNL Workday]과(와) Adobe Sign 간의 OAuth 관계 설정

## Adobe Sign 계정 활성화 {#activating-your-adobe-sign-account}

계정이 설정된 기존 고객은 [Adobe Sign for [!DNL Workday]](#config) 항목으로 건너뛸 수 있습니다.

Adobe Sign을 처음 사용하고 기존 로그인이 없는 고객의 경우, Adobe 온-보딩 전문가가 [!DNL Workday]에 대한 계정을 제공합니다. 완료되면 아래와 같이 확인 이메일을 받게 됩니다.

![Adobe Sign에서 보낸 시작 이메일 이미지](images/welcome-email-2020.png)

전자 메일의 지시에 따라 계정을 초기화하고 Adobe Sign [!UICONTROL Home] 페이지에 액세스해야 합니다.

![Adobe Sign 대시보드 페이지](images/classic-home.png)

## [!DNL Workday]에 대한 Adobe Sign 구성 {#config}

[!DNL Workday]에 대해 Adobe Sign을 구성하려면 Adobe Sign 시스템에서 다음 두 개의 전용 객체를 생성해야 합니다.

* **그룹  [!DNL Workday]**:  [!DNL Workday] 통합 기능을 사용하려면 Adobe Sign 계정에 전용 &quot;그룹&quot;이 필요합니다. Adobe Sign 그룹은 Adobe Sign의 [!DNL Workday] 사용량만 제어하는 데 사용됩니다. Salesforce.com 또는 Arriba와 같은 기타 잠재적 사용은 영향을 받지 않습니다. 전자 메일 알림은 [!DNL Workday] 그룹에서 표시되지 않으므로 [!DNL Workday] 사용자는 [!DNL Workday] 받은 편지함 내에서만 알림을 받습니다.

* **통합 키를 보유할 인증 사용자**: 그룹 [!DNL Workday] 에는 통합 키의 권한을 가진 그룹 수준 관리자가 하나만 있어야 합니다. 관리자는 개인 전자 메일 대신 `HR@MyDomain.com`과 같은 기능적인 전자 메일 주소를 사용하여 나중에 사용자가 비활성화될 위험을 줄이고 결과적으로 통합을 해제하는 것이 좋습니다.

### Adobe Sign에서 사용자 및 그룹 만들기 {#create-a-user-and-group-in-adobe-sign}

Adobe Sign에서 사용자를 만들려면:

1. 계정 관리자로 Adobe Sign에 로그인합니다..
1. **[!UICONTROL 계정]** > **[!UICONTROL 사용자]**&#x200B;로 이동합니다.
1. ![플러스 아이콘 이미지](images/icon_plus.png)를 클릭하여 새 사용자를 만듭니다.

   ![새 사용자 만들기로 이동 경로 이미지](images/navigate-to-group-unbranded.png)

1. 열리는 대화 상자에서 새 사용자 세부 정보를 제공합니다.

   * 액세스할 수 있는 기능 전자 메일을 제공하십시오.
   * 적절한 이름 및 성 값을 입력합니다.
   * 사용자 그룹에서 **[!UICONTROL 이 사용자에 대한 새 그룹 만들기]**&#x200B;를 선택합니다.
   * **[!UICONTROL 새 그룹 이름]**&#x200B;에 *[!DNL Workday]*&#x200B;와 같은 직관적인 이름을 지정하십시오.

   ![사용자 만들기 패널](images/create-user.png)

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   [!UICONTROL CREATED ]**상태의 새 사용자를 나열하는 ] 페이지로 돌아갑니다.**[!UICONTROL 

   ![새로 만든 사용자의 보기](images/post-user-creation.png)

&quot;작성됨&quot; 상태의 사용자의 전자 메일 주소를 확인하려면 다음과 같이 하십시오.

1. 새 사용자의 전자 메일에 로그인합니다.
2. &quot;Adobe Sign 시작&quot; 전자 메일을 찾습니다.
3. **[!UICONTROL 암호를 설정하려면 여기를 클릭하십시오]**.
4. 암호 설정.

전자 메일 주소를 확인하면 사용자의 상태가 [!UICONTROL CREATED]에서 [!UICONTROL ACTIVE]로 변경됩니다.

![활성화된 새 사용자의 이미지](images/actived-users-575.png)

### 인증 사용자 정의 {#define-the-authenticating-user}

[!DNL Workday] 그룹에서 새 사용자를 승격하려면 다음을 수행합니다.

1. [!UICONTROL 사용자] 페이지로 이동합니다(아직 없는 경우).
2. [!DNL Workday] 그룹에서 사용자를 두 번 클릭합니다.

   사용자 권한에 대한 [!UICONTROL 편집] 페이지가 열립니다.

3. **[!UICONTROL 그룹 관리자]**&#x200B;를 확인하십시오.
4. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

![](images/user-permissions-edit1-575.png)

## [!DNL Workday] 테넌트 구성 {#configure-workday}

[!DNL Workday] 테넌트와 Adobe Sign 간의 연결을 완료하려면 서비스 간에 신뢰할 수 있는 관계를 설정해야 합니다. 작업이 완료되면 Adobe Sign을 통해 서명 프로세스를 활성화하는 문서 검토 단계를 추가할 수 있습니다.

>[!NOTE]
>
>Adobe Sign은 [!DNL Workday] 환경 전체에서 Adobe Document Cloud로 낙인됩니다.

신뢰할 수 있는 관계를 설정하려면 다음을 수행하십시오.

1. 계정 관리자로 [!DNL Workday]에 로그인합니다.
1. **[!UICONTROL 테넌트 설정 편집 - 비즈니스 프로세스]** 페이지를 엽니다.
1. [!UICONTROL eSignature 구성] 섹션을 찾습니다.

   ![](images/esignature_configurations.png)

1. **[!UICONTROL Adobe]**&#x200B;에서 인증을 클릭합니다.

   OAuth2.0 인증 시퀀스가 시작됩니다.

1. 메시지가 표시되면 이전에 만든 Adobe 서명 그룹 관리자에 대한 자격 증명을 제공하십시오.
1. Adobe Sign 액세스를 승인합니다.

>[!NOTE]
>
>계속하기 전에 다른 Adobe Sign 인스턴스에서 완전히 로그아웃해야 합니다.

연결되면 Adobe 구성 사용 확인란이 설정되고 [!DNL Workday]으로 Adobe Sign을 사용할 수 있습니다.

### 검토 문서 단계 구성 {#configure-review}

문서 검토 단계의 문서는 다음 중 하나가 될 수 있습니다.

* 정적 문서
* 동일한 업무 프로세스 내의 문서 생성 단계에서 생성된 문서
* [!DNL Workday] 보고서 디자이너로 만든 서식 있는 보고서

[Adobe Text Tags](https://adobe.com/go/adobesign_text_tag_guide_kr)를 사용하여 Adobe Signing 특정 구성 요소의 모양과 위치를 제어할 수 있습니다. 비즈니스 프로세스 정의 내에 문서 원본이 지정되어야 합니다. 비즈니스 프로세스가 실행되는 동안 임시 문서를 업로드할 수 없습니다.

문서 검토 단계와 함께 Adobe Sign을 사용하는 것은 서명자 그룹을 직렬화할 수 있는 기능입니다. 이 기능 덕분에 차례로 서명하는 역할 기반의 그룹을 지정할 수 있습니다. Adobe Sign에서는 병렬 서명 그룹을 지원하지 않습니다.

문서 검토 단계를 구성하는 방법에 대한 자세한 내용은 [빠른 시작 안내서](https://adobe.com//go/adobesign_workday_quick_start){target=&quot;_blank&quot;}를 참조하십시오.

## 지원 {#support}

### [!DNL Workday] 지원 {#workday-support}

[!DNL Workday] 통합 소유자이며 통합 범위, 기능 요청 또는 통합의 일상적인 기능에서 발생하는 문제에 대한 질문을 받을 수 있는 첫 번째 담당자여야 합니다.

통합 문제를 해결하고 문서를 생성하는 방법은 다음 [!DNL Workday] 커뮤니티 문서를 참조하십시오.

* [eSignature 통합 문제 해결](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [문서 검토 단계](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [동적 문서 생성](https://community.workday.com/saml/login?destination=/articles/176443)
* [문서 생성 팁 제공](https://community.workday.com/node/183242)

### Adobe 서명 지원 {#adobe-sign-support}

Adobe Sign은 통합 파트너로서, 통합 과정에서 서명을 받지 못하거나 대기 중인 서명의 알림에 실패하는 경우에 문의해야 합니다.

Adobe Sign 고객은 담당 고객 성공 관리자(CSM)에게 지원을 요청해야 합니다. 또는 Adobe 기술 지원(전화: 1-866-318-4100)에 전화하여 제품 목록이 나오면 4번에 이어 2번(전화 안내에 따라)을 누르면 됩니다.

* [문서에 Adobe 텍스트 태그 추가](https://adobe.com/go/adobesign_text_tag_guide)
* [문서 구성 및 예](https://experienceleague.adobe.com/docs/dc-sign-integrations/using/workday/quick-start.html?lang=en){target=&quot;_blank&quot;} 검토

## 일반적인 질문 {#faq}

### 문서가 완전히 서명된 경우에도 [!DNL Workday] 내에서 상태가 업데이트되지 않는 이유는 무엇입니까? {#why-is-the-status-not-being-updated-within-workday-even-the-document-is-fully-signed}

Adobe Sign에 로그인한 후 후보자가 &#39;[!UICONTROL Submit]&#39; 단추를 클릭하지 않으면 [!DNL Workday]의 문서 상태가 반영되지 않을 수 있습니다.

[!DNL Workday] 작업에 따라 eSignature 서명 상태 확인: 프로세스를 시작하려면 연결된 받은 편지함 작업을 제출할 수 있습니다.

[!DNL Workday] 개발 기준: 원본 서명은 사용자가 문서에 서명한 후 받은 편지함 작업을 제출하는 경우에만 프로세스를 완료합니다. 서명 후 iframe이 닫히고 사용자가 [!UICONTROL Submit] 단추를 클릭하여 프로세스를 완료할 수 있는 동일한 작업으로 리디렉션됩니다.
