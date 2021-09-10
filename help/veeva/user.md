---
title: Veva Vault 사용 설명서
description: Veva Vault 고객 사용 설명서 - Veva와 Adobe Sign 통합 사용 방법
products: Adobe Sign
content-type: reference
locnotes: All languages; screenshots to follow what's there already (seems there is a mix within a given language version of the article)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 39a43637-af3f-432e-a784-8f472aa86df5
source-git-commit: 63a34c2d77ba7a262670da624c86a3730de0fdc5
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 1%

---

# [!DNL Veeva Vault]용 Adobe 서명: 사용 설명서 {#veeva-vault-user-guide}

[**Adobe Sign 지원 문의**](https://adobe.com/go/adobesign-support-center_kr)

이 문서는 [!DNL Veeva Vault] 고객이 [!DNL Veeva Vault] 통합을 위해 Adobe Sign을 사용하여 계약을 보내는 방법을 배우도록 돕기 위해 마련되었습니다.

## 개요 {#overview}

[!DNL Veeva Vault]과(와) Adobe Sign을 통합하면 법적 서명 또는 감사 가능한 문서 처리가 필요한 문서에 대한 서명 또는 승인을 얻을 수 있습니다.

서명을 위해 문서를 보내는 전반적인 과정은 이메일을 보내는 것과 비슷하기 때문에 대부분의 사용자들이 쉽게 채택할 수 있다.

Adobe Sign과 [!DNL Veeva Vault]의 통합으로 문서 및 서명 워크플로를 효율화하고 신속하게 처리할 수 있습니다. 통합 워크플로우를 사용하여 다음을 수행합니다.

* 달팽이 우편, 초과 근무 및 팩스 사용에 소요되는 시간과 자원을 절약합니다.
* [!DNL Veeva Vault]에서 전자 서명 또는 승인을 위한 계약을 보내고, 실시간 계약 내역에 액세스하고, 저장된 계약을 봅니다.
* 조직 전체에서 딜을 실시간으로 추적하고 계약을 보거나, 서명하거나, 취소하거나, 거부할 때 업데이트를 받습니다.
* 전 세계 50개 이상의 로캘에서 20개 이상의 언어로 로그인하고 팩스 백 서비스를 지원합니다.
* 옵션을 보내기 위해 다시 사용할 수 있는 계약 템플릿을 만듭니다.

## [!DNL Veeva Vault]에 대한 Adobe Sign을 사용하여 계약 보내기 {#send-sign-vault-agreement}

Veva용 Adobe Sign을 사용하여 계약을 보내려면 다음과 같이 하십시오.

1. [[!DNL Veeva Vault] 로그인 페이지](https://login.veevavault.com/)로 이동하여 사용자 이름과 암호를 입력하십시오. 아래와 같이 저장소의 홈 페이지가 열립니다.

   ![](images/vault-home.png)

1. **[!UICONTROL 라이브러리]** 탭을 선택한 다음 오른쪽 상단 모서리에서 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

   ![](images/create-library.png)

1. **[!UICONTROL 업로드 및 계속]**&#x200B;을 선택합니다.

1. 로컬 드라이브에서 문서를 업로드합니다.

1. 나타나는 대화 상자에서 **[!UICONTROL Type]**&#x200B;을 *[!UICONTROL Clinical]*&#x200B;으로 선택한 다음 필요한 경우 **[!UICONTROL Subtype]** 및 **[!UICONTROL Classification]**&#x200B;을 선택합니다.

   ![](images/choose-document-type.png)

1. **[!UICONTROL 확인]**&#x200B;을 선택하여 대화 상자를 닫습니다.

1. **[!UICONTROL 다음]**&#x200B;을 선택합니다.

1. 표시되는 창에서 메타데이터 섹션의 모든 필수 필드를 입력하고 **[!UICONTROL 저장]**&#x200B;을 선택합니다.

   ![](images/metadata-details.png)

1. 아래와 같이 **[!UICONTROL Draft]** 상태로 테스트 문서를 만듭니다.

   ![](images/document-draft.png)

1. 오른쪽 상단 모서리에서 ![기어 아이콘](images/icon-gear.png) 드롭다운 메뉴를 선택하고 **[!UICONTROL 시작 검토]**&#x200B;를 선택합니다.

   ![](images/start-review.png)

1. **[!UICONTROL 검토자]** 및 **[!UICONTROL 검토 기한]**&#x200B;을 선택합니다.

1. **[!UICONTROL 시작]**&#x200B;을 선택합니다. 문서 상태가 [!UICONTROL IN REVIEW]로 변경됩니다.

   ![](images/in-review.png)

1. 검토자 대신 할당된 작업을 완료합니다. 완료되면 문서 상태가 [!UICONTROL REVIEWED]로 변경됩니다.

   ![](images/reviewed-status.png)

1. ![기어 아이콘](images/icon-gear.png) 드롭다운 메뉴를 선택하고 **[!UICONTROL Adobe Sign]**&#x200B;을 선택합니다.

   ![](images/select-adobe-sign.png)

1. 자격 증명 모음에서 열리는 iFrame 창에서 받는 사람의 전자 메일 주소를 입력하고 **[!UICONTROL 다음]**&#x200B;을 선택합니다.

   ![](images/iframe.png)

1. 문서가 처리되면 오른쪽 패널에서 서명 필드를 끌어 놓은 다음 **[!UICONTROL 보내기]**&#x200B;를 선택합니다.

   ![](images/add-signature-fields.png)

1. 서명을 위해 문서를 수신자에게 보냅니다. 받는 사람이 문서 전자 메일을 받으면 문서 상태가 [!UICONTROL 검토됨]에서 [!UICONTROL Adobe Signing]으로 변경됩니다.

   ![](images/in-adobe-signing.png)

1. 모든 서명이 Adobe Sign에서 캡처되고 완료되면 자격 증명 모음의 문서 상태가 [!UICONTROL 승인됨]으로 변경됩니다.

1. **[!UICONTROL 문서 파일]** 옵션을 선택하고 저장소에서 **[!UICONTROL 변환]** 섹션을 확장합니다. 문서가 승인됨 상태가 되면 &#39;Adobe Sign Rendition&#39;이라는 새 변환이 자동으로 만들어집니다.

   ![](images/document-files.png)

1. 수신 서명의 유효성을 검사하려면 Adobe 서명 변환을 다운로드합니다.

   ![](images/verify-signature.png)

## [!DNL Veeva Vault]에 대한 Adobe Sign을 사용하여 계약 취소 {#cancel-sign-vault-agreement}

1. [[!DNL Veeva Vault] 로그인 페이지](https://login.veevavault.com/)로 이동하여 사용자 이름과 암호를 입력하십시오. 아래와 같이 저장소의 홈 페이지가 열립니다.

   ![](images/vault-home.png)

1. **[!UICONTROL 라이브러리]** 탭을 선택한 다음 문서를 선택합니다. 문서 상태는 다음과 같습니다. [!UICONTROL Adobe Sign Draft], [!UICONTROL Adobe Sign Authoring] 또는 [!UICONTROL Adobe Signing]에서

   ![](images/document-adobe-sign-authoring.png)

1. **[!UICONTROL Adobe Sign]** 취소를 선택합니다.

   ![](images/cancel-document.png)

1. 웹 작업을 트리거하고 [!UICONTROL Vault]에서 iFrame 창을 로드합니다.

   ![](images/cancelled-document.png)

1. 문서 상태는 자동으로 [!UICONTROL Review]로 변경됩니다.

   ![](images/cancel-reviewed.png)

문서 상태가 [검토]로 변경된 후 다시 서명을 위해 문서를 보낼 수 있습니다.
