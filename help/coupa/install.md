---
title: Coupa 설치 안내서
description: Coupa BSM Suite와 Adobe Sign 통합 활성화를 위한 설치 안내서
product: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Acrobat Sign, Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 12c91be5-afec-4918-a8fc-ceb33bedf98b
source-git-commit: b326a9afa2c16333d390cac3b30a2c7c741a4360
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 6%

---

# [!DNL Coupa] 설치 안내서{#coupa-installation-guide}

[**Adobe Sign 지원 문의**](https://adobe.com/go/adobesign-support-center_kr)

## 개요 {#overview}

이 문서에서는 통합하도록 Adobe Sign 계정을 구성하는 방법에 대해 설명합니다 [!DNL Coupa BSM Suite] 서명을 받기 위한 인스턴스입니다.

사전 요구 사항:

* Adobe Sign Enterprise 구독 [Adobe Sign Developer Edition](https://www.adobe.com/sign/developer-form.html), 또는 [Adobe Sign Enterprise 평가판](https://www.adobe.com/sign/business.html)
* Adobe Sign 관리자 액세스
* [!DNL Coupa BSM Suite] 표준 또는 고급 인스턴스

통합을 완성하기 위한 고급 단계는 다음과 같습니다.

* 에 사용할 Adobe Sign 그룹 구성 [!DNL Coupa BSM Suite]
* Connect [!DNL Coupa BSM Suite] Adobe Sign
* 알림을 위한 Adobe Sign Webhook 만들기 [!DNL Coupa BSM Suite] 인스턴스

## Adobe Sign 그룹 구성 [!DNL Coupa BSM Suite] {#configure-adobe-sign-for-coupa}

Adobe Sign 전용으로 사용 [!DNL Coupa] 조직 내에서 책임자는 다음에 대한 Adobe Sign 그룹을 [!DNL Coupa BSM Suite] 사용합니다. 이 Adobe Sign 그룹에는 서비스 계정으로 사용되는 단일 그룹 관리자 사용자 계정이 있어야 합니다. 이 서비스 계정은 모든 서명 요청에 사용되므로, 예를 들어 익명으로 유지되어야 합니다. `Legal@xyz.com`, `Purchasing@xyz.com`, 또는 `CoupaCLM@xyz.com`,(예: `Bob.Smith@xyz.com`.

### Adobe Sign에서 그룹 및 사용자 만들기 {#create-sign-user-group}

Adobe Sign에서 사용자를 만들려면:

1. 계정 관리자로 Adobe Sign에 로그인합니다..
1. 다음으로 이동 **[!UICONTROL 계정]** > **[!UICONTROL 사용자]**.
1. 새 사용자를 만들려면 ![플러스 아이콘 이미지](images/icon_plus.png) 아이콘을 클릭합니다.
1. 열리는 대화 상자에서 새 사용자 세부 정보를 입력합니다.

   1. 액세스할 수 있는 기능 이메일을 입력합니다.

      * 이 사용자는 OAuth 관계를 설정하고 유지합니다.
      * 전자 메일 주소는 확인을 위한 실제 주소여야 합니다.
   1. 에 적절한 값을 입력합니다. [!UICONTROL 이름] 및 [!UICONTROL 성].
   1. 에 [!UICONTROL 기본 그룹] 필드, 선택 **[!UICONTROL 이 사용자의 새 그룹 만들기]**.
   1. 에 [!UICONTROL 새 그룹 이름] 필드에 *[!DNL Coupa BSM Suite]*.

   ![사용자 만들기 패널](images/create-user.png)

1. 선택 **[!UICONTROL 저장]**.

   세부 정보를 저장하면 [!UICONTROL 사용자] 페이지에 [!UICONTROL 생성됨] 상태.

   ![새로 생성된 사용자 보기](images/post-user-creation.png)

   추가 [!UICONTROL 생성됨] 상태는 사용자가 아직 전자 메일 주소를 확인하지 않았음을 나타냅니다.

1. 전자 메일 주소를 확인하려면 다음을 수행하십시오.
   1. 새 사용자의 전자 메일에 로그인합니다.
   2. &quot;Adobe Sign 시작&quot; 이메일을 찾습니다. 필요한 경우 스팸/정크 폴더를 확인하십시오.
   3. **[!UICONTROL 암호를 설정하려면 여기를 클릭하십시오]**&#x200B;라고 적힌 부분을 클릭합니다.
   4. 암호 설정.

   전자 메일 주소를 확인하면 사용자의 상태가 [!UICONTROL 생성됨] 에 [!UICONTROL 활성].

   ![새로 활성화된 사용자의 이미지](images/active-user.png)

### 인증 사용자 정의 {#define-authenticating-user}

그룹 및 해당 그룹에 사용자를 생성하면 사용자를 &#39;그룹 관리자&#39;로 만들어야 합니다.

새 사용자를 [!DNL Coupa BSM Suite] 그룹:

1. 다음 위치로 이동합니다. [!UICONTROL 사용자] 페이지(아직 없는 경우)
2. 사용자를 두 번 클릭합니다.

   그러면 [!UICONTROL 편집] 페이지를 참조하십시오.

3. 그룹 멤버십 섹션에서 **[!UICONTROL 그룹 관리자]** 및 **[!UICONTROL 전송 가능]** 있습니다.
4. 선택 취소 **[!UICONTROL 사용자가 계정 관리자입니다.]** 및 **[!UICONTROL 사용자가 문서에 서명할 수 있음]** 있습니다.
5. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   ![사용자 설정 이미지](images/user-settings.png)

## 구성 [!DNL Coupa BSM Suite] 인스턴스 {#configure-coupa}

다음 중 하나를 사용하여 [!DNL Coupa BSM Suite ] 인스턴스와 Adobe Sign, 서비스 간에 신뢰할 수 있는 관계를 설정해야 합니다.

를 구성하려면 [!DNL Coupa BSM Suite]:

1. PDF에 [!DNL Coupa BSM Suite] 인스턴스를 위에서 만든 Adobe Sign 서비스 계정으로 이동합니다.
1. Adobe Sign Webhook 인스턴스를 만들어 계약 업데이트에 대해 Coupa BSM Suite 인스턴스에 알립니다.

을 연결하는 방법에 대한 자세한 내용은 [!DNL Coupa BSM Suite] webhook 생성 및 등록 방법은 [Adobe Sign Coupa BSM Suite 인스턴스 지원 문서](https://success.coupa.com/Support/Docs/Power_Apps/CLM_Standard/Signing_and_Approvals/Enable_E-Signatures_Through_Adobe_Sign_and_DocuSign){target=&quot;_blank&quot;}.

## 만들기 [!DNL Webhook] Adobe Sign {#create-webhook}

Coupa CLM 통합은 Adobe Sign의 Webhook 알림을 사용하여 계약 상태에 대한 업데이트를 보냅니다. Webhook 설정을 완료하는 것이 중요합니다. 그렇지 않으면 서명을 위해 전송된 계약서가 불완전하게 유지되거나 서명된 계약서가 Coupa CLM으로 다시 배달되지 않습니다.

Adobe Sign에서 Webhook을 만들려면:

1. 위에서 생성된 그룹 관리자 사용자를 사용하여 Adobe Sign에 로그인합니다. 예를 들면 다음과 같습니다 `coupaclm@MyDomain.com`.

1. 다음으로 이동 **그룹** > **웹 후크**.

   ![사용자 설정 이미지](images/webhook-login.png)

1. 새 연결을 만들려면 ![플러스 아이콘 이미지](images/icon_plus.png) 아이콘을 클릭합니다.

1. 표시되는 만들기 대화 상자에서 필수 필드를 입력합니다.

   **참고:** Coupa에서 Webhook 핸들러의 URL을 가져와야 합니다.

   ![사용자 설정 이미지](images/webhook-create.png)

1. 필요한 통지 매개변수를 선택합니다.

1. 선택 **저장**.

## 지원 {#support}

### [!DNL Coupa BSM Suite] 지원 {#coupa-support}

[!DNL Coupa BSM Suite ] 통합 소유자이며 통합 범위, 기능 요청 또는 통합의 일상적인 기능에 대한 질문에 대한 첫 번째 연락처여야 합니다.

질문이 있는 경우 [Coupa 지원](https://success.coupa.com/Support/Welcome_to_Coupa_Support){target=&quot;_blank&quot;}.

### Adobe Sign 지원 {#adobe-sign-support}

Adobe Sign은 통합 파트너이며 통합에서 서명을 받지 못하거나 보류 중인 서명 통지에 실패하는 경우 연락해야 합니다.

Adobe Sign 사용 또는 구성에 대한 지원이 필요한 경우 고객 성공 관리자(CSM)에게 문의하거나 [Adobe Sign 지원](https://adobe.com/go/adobesign-support-center).

Adobe Sign 관리자는 티켓을 열고 도움말(?)을 통해 지원을 받을 수도 있습니다. 을 클릭합니다.

![Adobe Sign 포털 도움말 이미지](images/sign-portal-help.png)
