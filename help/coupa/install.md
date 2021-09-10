---
title: Coupa 설치 가이드
description: Coupa BSM Suite와 Adobe Sign 통합을 활성화하는 설치 안내서
product: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 12c91be5-afec-4918-a8fc-ceb33bedf98b
source-git-commit: 623307e86f1b32edfbfa59dbd636ff74a6d09b62
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 6%

---

# [!DNL Coupa] 설치 안내서{#coupa-installation-guide}

[**Adobe Sign 지원 문의**](https://adobe.com/go/adobesign-support-center_kr)

## 개요 {#overview}

서명을 받기 위해 [!DNL Coupa BSM Suite] 인스턴스를 통합하도록 Adobe Sign 계정을 구성하는 방법에 대해 설명합니다.

사전 요구 사항:

* Adobe Sign Enterprise, [Adobe Sign Developer Edition](https://www.adobe.com/sign/developer-form.html) 또는 [Adobe Sign Enterprise Trial](https://www.adobe.com/sign/business.html) 구독
* Adobe 서명 관리자 액세스
* [!DNL Coupa BSM Suite] 표준 또는 고급 인스턴스

통합을 완료하는 상위 단계는 다음과 같습니다.

* [!DNL Coupa BSM Suite]과(와) 함께 사용할 Adobe Sign Group 구성
* [!DNL Coupa BSM Suite]을(를) Adobe Sign에 연결
* [!DNL Coupa BSM Suite] 인스턴스를 알리는 Adobe Sign webhook 만들기

## [!DNL Coupa BSM Suite]에 대한 Adobe Sign Group 구성 {#configure-adobe-sign-for-coupa}

조직 내에서 [!DNL Coupa]에 대해 Adobe Sign을 전용으로 사용하려면 관리자가 [!DNL Coupa BSM Suite] 사용을 위해 특별히 Adobe Sign 그룹을 만들어야 합니다. 이 Adobe 서명 그룹에는 서비스 계정으로 사용되는 단일 그룹 관리자 사용자 계정이 있어야 합니다. 이 서비스 계정은 모든 서명 요청에 사용되므로 `Bob.Smith@xyz.com` 등의 개인 계정이 아닌 `Legal@xyz.com`, `Purchasing@xyz.com` 또는 `CoupaCLM@xyz.com` 등의 익명으로 보관해야 합니다.

### Adobe Sign에서 그룹 및 사용자 만들기 {#create-sign-user-group}

Adobe Sign에서 사용자를 만들려면:

1. 계정 관리자로 Adobe Sign에 로그인합니다..
1. **[!UICONTROL 계정]** > **[!UICONTROL 사용자]**&#x200B;로 이동합니다.
1. 새 사용자를 만들려면 ![플러스 아이콘 image](images/icon_plus.png) 아이콘을 클릭합니다.
1. 열리는 대화 상자에서 새 사용자 세부 정보를 제공합니다.

   1. 액세스할 수 있는 기능 전자 메일을 제공하십시오.

      * 이 사용자는 OAuth 관계를 설정하고 유지 관리합니다.
      * 전자 메일 주소는 확인을 위한 실제 주소여야 합니다.
   1. [!UICONTROL First Name] 및 [!UICONTROL Last Name]에 적절한 값을 입력하십시오.
   1. [!UICONTROL 주 그룹] 필드에서 **[!UICONTROL 이 사용자에 대한 새 그룹 만들기]**&#x200B;를 선택합니다.
   1. [!UICONTROL 새 그룹 이름] 필드에서 *[!DNL Coupa BSM Suite]*&#x200B;와 같은 직관적인 그룹 이름을 제공합니다.

   ![사용자 만들기 패널](images/create-user.png)

1. **[!UICONTROL Save]**&#x200B;를 선택합니다.

   세부 정보를 저장하면 [!UICONTROL 사용자] 페이지에 [!UICONTROL CREATED] 상태의 새 사용자가 표시됩니다.

   ![새로 만든 사용자의 보기](images/post-user-creation.png)

   [!UICONTROL CREATED] 상태는 사용자가 아직 전자 메일 주소를 확인하지 않았음을 나타냅니다.

1. 전자 메일 주소를 확인하려면 다음과 같이 하십시오.
   1. 새 사용자의 전자 메일에 로그인합니다.
   2. &quot;Adobe Sign 시작&quot; 전자 메일을 찾습니다. 필요한 경우 스팸/정크 폴더를 확인합니다.
   3. **[!UICONTROL 암호를 설정하려면 여기를 클릭하십시오]**&#x200B;라고 적힌 부분을 클릭합니다.
   4. 암호 설정.

   전자 메일 주소를 확인하면 사용자의 상태가 [!UICONTROL CREATED]에서 [!UICONTROL ACTIVE]로 변경됩니다.

   ![활성화된 새 사용자의 이미지](images/active-user.png)

### 인증 사용자 정의 {#define-authenticating-user}

그룹과 사용자를 만든 후에는 사용자를 &#39;그룹 관리자&#39;로 만들어야 합니다.

[!DNL Coupa BSM Suite] 그룹에서 새 사용자를 승격하려면 다음을 수행합니다.

1. [!UICONTROL 사용자] 페이지로 이동합니다(아직 없는 경우).
2. 사용자를 두 번 클릭합니다.

   사용자 권한에 대한 [!UICONTROL 편집] 페이지를 엽니다.

3. 그룹 구성원 섹션 아래에서 **[!UICONTROL 그룹 관리]** 및 **[!UICONTROL 보내기 가능]** 옵션을 선택합니다.
4. **[!UICONTROL 사용자는 계정 admin]**&#x200B;이고 **[!UICONTROL 사용자는 문서]** 옵션에 서명할 수 있습니다.
5. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   ![사용자 설정 이미지](images/user-settings.png)

## [!DNL Coupa BSM Suite] 인스턴스 구성 {#configure-coupa}

[!DNL Coupa BSM Suite ] 인스턴스와 Adobe Sign 간의 연결을 완료하려면 서비스 간에 신뢰할 수 있는 관계를 설정해야 합니다.

[!DNL Coupa BSM Suite]을(를) 구성하려면 다음과 같이 하십시오.

1. [!DNL Coupa BSM Suite] 인스턴스를 위에서 만든 Adobe Sign 서비스 계정에 연결합니다.
1. 계약에 대한 업데이트를 Coupa BSM Suite 인스턴스에 알리는 Adobe Sign webhook 인스턴스를 만듭니다.

[!DNL Coupa BSM Suite]에 연결하는 방법과 webhook을 만들고 등록하는 방법에 대한 자세한 내용은 [Adobe Sign Coupa BSM Suite Instance 지원 설명서](https://success.coupa.com/Support/Docs/Power_Apps/CLM_Standard/Signing_and_Approvals/Enable_E-Signatures_Through_Adobe_Sign_and_DocuSign){target=&quot;_blank&quot;}을(를) 참조하십시오.

## Adobe Sign에서 [!DNL Webhook] 만들기 {#create-webhook}

Coupa CLM 통합은 Adobe Sign의 webhook 알림을 사용하여 계약 상태에 대한 업데이트를 보냅니다. 서명을 위해 보낸 계약이 완료되지 않거나 서명된 계약이 Coupa CLM으로 다시 전달되지 않는 경우 Webhook 설정을 완료하는 것이 중요합니다.

Adobe Sign에서 웹 후크를 만들려면 다음과 같이 하십시오.

1. 위에 만든 그룹 관리자 사용자(예: `coupaclm@MyDomain.com`)를 사용하여 Adobe Sign에 로그인합니다.

1. **그룹** > **웹 후크**&#x200B;로 이동합니다.

   ![사용자 설정 이미지](images/webhook-login.png)

1. 새 연결을 만들려면 ![plus 아이콘 image](images/icon_plus.png) 아이콘을 선택합니다.

1. 열리는 만들기 대화 상자에서 필요한 필드를 입력합니다.

   **참고:** Coupa에서 webhook 처리기의 Url을 가져와야 합니다.

   ![사용자 설정 이미지](images/webhook-create.png)

1. 필요한 통지 매개변수를 선택합니다.

1. **Save**&#x200B;를 선택합니다.

## 지원 {#support}

### [!DNL Coupa BSM Suite] 지원 {#coupa-support}

[!DNL Coupa BSM Suite ] 통합 소유자이며 통합 범위, 기능 요청 또는 통합의 일상적인 기능에서 발생하는 문제에 대한 질문을 받을 수 있는 첫 번째 담당자여야 합니다.

쿼리에 대해서는 [Coupa Support](https://success.coupa.com/Support/Welcome_to_Coupa_Support){target=&quot;_blank&quot;}에 문의하십시오.

### Adobe 서명 지원 {#adobe-sign-support}

Adobe Sign은 통합 파트너이며 통합에서 서명을 받지 못하거나 보류 중인 서명에 대한 알림이 실패할 경우 연락해야 합니다.

Adobe Sign 사용 또는 구성에 대한 도움말을 보려면 CSM(Customer Success Manager)에 문의하거나 [Adobe Sign 지원](https://adobe.com/go/adobesign-support-center)에 문의하십시오.

Adobe Sign 관리자는 티켓을 열고 도움말(?)을 통해 지원을 받을 수도 있습니다. Adobe Sign 포털의 오른쪽 위에 있습니다.

![Adobe Sign 포털 도움말 이미지](images/sign-portal-help.png)
