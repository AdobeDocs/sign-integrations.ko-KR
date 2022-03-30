---
title: Veeva Vault 사용 설명서
description: Veeva Vault 고객 사용 설명서에서 Adobe Sign과 Veeva의 통합 사용 방법
products: Adobe Sign
content-type: reference
locnotes: All languages; screenshots to follow what's there already (seems there is a mix within a given language version of the article)
type: Documentation
solution: Acrobat Sign
role: User, Developer
topic: Integrations
exl-id: 39a43637-af3f-432e-a784-8f472aa86df5
source-git-commit: 4d73ff36408283805386bd3266b683bc187d6031
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 0%

---

# Adobe Acrobat Sign for [!DNL Veeva Vault]: 사용 안내서 {#veeva-vault-user-guide}

[**Adobe Acrobat Sign 지원 문의**](https://adobe.com/go/adobesign-support-center_kr)

이 문서는 [!DNL Veeva Vault] 고객은 Adobe Acrobat Sign for [!DNL Veeva Vault] 계약서 전송을 위한 통합.

## 개요 {#overview}

Adobe Acrobat Sign과 [!DNL Veeva Vault] 에서는 법적 서명 또는 감사 가능한 문서 처리가 필요한 모든 문서에 대해 서명 또는 승인을 얻는 프로세스를 용이하게 합니다.

서명을 위해 문서를 보내는 전체적인 프로세스는 이메일을 보내는 것과 유사하므로 대부분의 사용자가 쉽게 채택할 수 있습니다.

Adobe Acrobat Sign과 [!DNL Veeva Vault] 문서 및 서명 워크플로우를 간소화하고 가속화합니다. 통합 작업 과정을 사용하여 다음을 수행할 수 있습니다.

* 스네일 메일, 오버나이트 또는 팩스 전송에 소요되는 시간과 리소스를 절약할 수 있습니다.
* 전자 서명 또는 승인을 위해 계약서를 [!DNL Veeva Vault]을 누르고 실시간 계약 내역에 액세스하고 저장된 계약을 확인할 수 있습니다.
* 조직 전체에서 거래를 실시간으로 추적하고 계약을 조회, 서명, 취소 또는 거절할 때 업데이트를 받을 수 있습니다.
* 20개 이상의 언어로 로그인하고 전 세계 50개 이상의 로케일에서 팩스 회신 서비스를 지원합니다.
* 전송 옵션에 대해 재사용 가능한 계약 템플릿을 만듭니다.

## Adobe Acrobat 서명을 사용하여 계약 보내기 [!DNL Veeva Vault] {#send-sign-vault-agreement}

Veeva용 Adobe Acrobat Sign을 사용하여 계약서를 보내려면:

1. 다음으로 이동 [[!DNL Veeva Vault] 로그인 페이지](https://login.veevavault.com/) 사용자 이름과 암호를 입력합니다. 아래와 같이 저장소의 홈 페이지가 열립니다.

   ![](images/vault-home.png)

1. 선택 **[!UICONTROL 라이브러리]** 탭을 선택한 다음 **[!UICONTROL 만들기]** 을 클릭합니다.

   ![](images/create-library.png)

1. 선택 **[!UICONTROL 업로드 및 계속]**.

1. 로컬 드라이브에서 문서를 업로드합니다.

1. 표시되는 대화 상자에서 **[!UICONTROL 유형]** 만큼 *[!UICONTROL 임상]* 그런 다음 **[!UICONTROL 하위 유형]** 및 **[!UICONTROL 분류]**&#x200B;를 클릭합니다(필요한 경우).

   ![](images/choose-document-type.png)

1. 대화 상자를 닫으려면 **[!UICONTROL 확인]**.

1. 선택 **[!UICONTROL 다음]**.

1. 표시되는 창에서 메타데이터 섹션의 모든 필수 필드를 채우고 **[!UICONTROL 저장]**.

   ![](images/metadata-details.png)

1. 테스트 문서를 **[!UICONTROL 초안]** 상태(아래 참조)

   ![](images/document-draft.png)

1. 오른쪽 상단에서 ![톱니바퀴 아이콘](images/icon-gear.png) 드롭다운 메뉴 및 선택 **[!UICONTROL 검토 시작]**.

   ![](images/start-review.png)

1. 다음을 선택합니다. **[!UICONTROL 검토자]** 및 **[!UICONTROL 검토 기한]**.

1. 선택 **[!UICONTROL 시작]**. 문서 상태 가 다음으로 변경됩니다. [!UICONTROL 검토 중].

   ![](images/in-review.png)

1. 검토자 대신 할당된 작업을 완료합니다. 완료되면 문서 상태가 로 변경됩니다. [!UICONTROL 검토됨].

   ![](images/reviewed-status.png)

1. 선택 ![톱니바퀴 아이콘](images/icon-gear.png) 드롭다운 메뉴 및 선택 **[!UICONTROL Adobe Sign]**.

   ![](images/select-adobe-sign.png)

1. Adobe Acrobat Sign 계정에서 UMG(다중 그룹의 사용자) 기능이 활성화되어 있고 발신자가 다중 그룹에 속한 경우 아래와 같은 대화 상자가 표시됩니다. 대화 상자에서 그룹을 선택한 다음 **[!UICONTROL 확인]**.

   ![](images/umg-dialog.png)

1. 자격 증명 모음에서 열리는 iFrame 창에서 수신자의 전자 메일 주소를 입력하고 **[!UICONTROL 다음]**.

   ![](images/iframe.png)

   **참고:** 전송자의 전자 메일에 대한 Adobe Acrobat Sign 사용자 계정이 없는 경우 아래와 같이 iFrame 창에 메시지가 표시됩니다. 또한 사용자에게 계정을 활성화하는 지침이 포함된 이메일을 보냅니다.

   ![](images/iFrame-registration-message.png)

   ![](images/iFrame-confirm-email.png)

   그러나 *Sign 사용자 자동 프로비저닝* 기능이 비활성화되고, Adobe Acrobat Sign 사용자 생성이 실패하며, iFrame 창에 사용자에게 Adobe Acrobat Sign 계정 관리자에게 문의하라는 메시지가 표시됩니다. Adobe Acrobat Sign 계정 관리자는 다음 작업 중 하나를 수행할 수 있습니다.

   * 활성화 *Sign 사용자 자동 프로비저닝* 계정에서 사용할 수 있습니다.
   * Veeva Vault Adobe Acrobat Sign 통합 기능을 사용하기 전에 Adobe Acrobat Sign에서 사용자를 작성합니다.

   ![](images/iFrame-contact-administrator.png)

1. 문서가 처리되면 오른쪽 패널에서 서명 필드를 드래그하여 놓고 **[!UICONTROL 전송]**.

   ![](images/add-signature-fields.png)

1. 서명을 위해 수신자에게 문서를 전송합니다. 수신자가 문서 전자 메일을 받으면 문서 상태가 [!UICONTROL 검토됨] 에 [!UICONTROL Adobe 서명 중].

   ![](images/in-adobe-signing.png)

1. Adobe Acrobat Sign에서 모든 서명이 캡처되고 완료되면 보관소의 문서 상태가 로 변경됩니다. [!UICONTROL 승인됨].

1. 선택 **[!UICONTROL 문서 파일]** option 키를 누른 상태에서 **[!UICONTROL 변환]** 섹션을 참조하십시오. 문서가 승인됨 상태가 되면 &#39;Adobe Sign Rendition&#39;이라는 변환이 자동으로 만들어집니다.

   ![](images/document-files.png)

1. 수신자 서명의 유효성을 확인하기 위해 Adobe Sign 렌디션을 다운로드합니다.

   ![](images/verify-signature.png)

## Adobe Acrobat Sign for [!DNL Veeva Vault] {#cancel-sign-vault-agreement}

1. 다음으로 이동 [[!DNL Veeva Vault] 로그인 페이지](https://login.veevavault.com/) 사용자 이름과 암호를 입력합니다. 아래와 같이 저장소의 홈 페이지가 열립니다.

   ![](images/vault-home.png)

1. 선택 **[!UICONTROL 라이브러리]** 을 누른 다음 문서를 선택합니다. 문서 상태는 다음과 같습니다. [!UICONTROL Adobe Sign Draft에서], [!UICONTROL Adobe Sign 작성에서], 또는 [!UICONTROL Adobe 서명 중].

   ![](images/document-adobe-sign-authoring.png)

1. 선택 **[!UICONTROL Adobe Sign 취소]**.

   ![](images/cancel-document.png)

1. 웹 액션을 트리거하고 [!UICONTROL Vault].

   ![](images/cancelled-document.png)

1. 문서 상태가 자동으로 [!UICONTROL 검토].

   ![](images/cancel-reviewed.png)

문서 상태가 검토로 변경되면 서명을 위해 다시 보낼 수 있습니다.
