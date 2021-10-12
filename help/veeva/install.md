---
title: '[!DNL Veeva Vault] 설치 안내서'
description: Veva와 Adobe Sign 통합을 활성화하는 설치 안내서
product: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 5d61a428-06e4-413b-868a-da296532c964
source-git-commit: b6925abdeb7912ae17161663a86637d9913de1ec
workflow-type: tm+mt
source-wordcount: '3089'
ht-degree: 2%

---

# [!DNL Veeva Vault] 설치 안내서{#veeva-installation-guide}

[**Adobe Sign 지원 문의**](https://adobe.com/go/adobesign-support-center_kr)

## 개요 {#overview}

이 문서에서는 [!DNL Veeva Vault] 플랫폼과 Adobe Sign의 통합을 설정하는 방법에 대해 설명합니다. [!DNL Veeva Vault] 생명 과학을 위해 구축된 ECM(엔터프라이즈 컨텐츠 관리) 플랫폼입니다. &quot;저장소&quot;는 규정 자료 작성, 연구 보고, 응용 프로그램 승인, 일반 계약 등에 사용되는 일반적인 컨텐츠 및 데이터 저장소입니다. 단일 엔터프라이즈에는 별도로 관리해야 하는 &#39;저장소&#39;가 여러 개 있을 수 있습니다.

통합을 완료하는 상위 단계는 다음과 같습니다.

* Adobe Sign에서 관리 계정 활성화(신규 고객만 해당)
* 객체를 생성하여 Vault에서 계약 수명 주기의 기록을 추적합니다.
* 새 보안 프로필을 만듭니다.
* [!DNL Veeva Vault] 통합 사용자를 보유하도록 Adobe Sign에서 그룹을 구성합니다.
* 문서 필드 및 변환을 만듭니다.
* 웹 작업을 구성하고 문서 주기를 업데이트합니다.
* 문서 유형 사용자 및 사용자 역할 설정을 만듭니다.

>[!NOTE]
>
>Adobe Sign 관리자는 Adobe Sign 내에서 Adobe Sign 설정 단계를 수행해야 합니다.

## 구성 [!DNL Veeva Vault]

[!DNL Veeva Vault]을(를) Adobe Sign과 통합하도록 구성하려면 Vault에서 계약 수명 주기의 기록을 추적하는 데 도움이 되는 특정 객체를 만듭니다. 관리자가 다음 개체를 만들어야 합니다.

* 서명
* 서명자
* 서명 이벤트
* 프로세스 락커

### 서명 개체 만들기  {#create-signature-object}

서명 개체는 계약 관련 정보를 저장하기 위해 만들어집니다. Signature 개체는 다음과 같은 특정 필드 아래의 정보를 포함하는 데이터베이스입니다.

**서명 개체 필드**

| 필드 | 레이블 | 유형 | 설명 |
| --- | --- | ---| --- | 
| external_id__c | 계약 ID | 문자열(100) | Adobe Sign의 고유한 계약 ID를 보관합니다. |
| 파일_해시_c | 파일 해시 | 문자열(50) | Adobe Sign으로 전송된 파일의 md5 chcksum을 보관합니다. |
| 이름__v | 이름 | 문자열(128) | 계약명을 보관합니다. |
| sender__c | 발신자 | 개체(사용자) | 계약을 작성한 저장소 사용자에 대한 참조를 보관합니다. |
| signature_status__c | 서명 상태 | 문자열(75) | Adobe Sign에서 계약 상태를 유지합니다. |
| signature_type__c | 서명 유형 | 문자열(20) | Adobe Sign(WRITTEN 또는 ESIGN)에서 계약의 서명 유형을 유지합니다. |
| 시작_날짜_c | 시작 날짜 | DateTime | 서명을 위해 계약을 보낸 날짜 |
| 취소_날짜__c | 취소 날짜 | 날짜 시간 | 계약이 취소된 일자를 보류합니다. |
| 완료_날짜_c | 완료 날짜 | 날짜 시간 | 계약이 완료된 일자를 보류합니다. |
| viewable_rendition_used__c | 사용 가능한 변환 | 부울 | 보기가능 변환이 서명을 위해 전송되었는지 여부를 나타내는 플래그입니다. (기본적으로 true) |

![서명 개체 세부 정보 이미지](images/signature-object-details.png)

### 서명자 객체 만들기 {#create-signatory-object}

서명자 객체는 계약의 참여자와 관련된 정보를 저장하기 위해 만들어집니다. 여기에는 다음과 같은 특정 필드에 대한 정보가 포함됩니다.

**서명자 객체 필드**

| 필드 | 레이블 | 유형 | 설명 |
| --- | --- | ---| --- | 
| 전자 메일__c | 전자 메일 | 문자열(120) | Adobe Sign의 고유한 계약 ID를 보관합니다. |
| external_id__c | 참가자 ID | 문자열(80) | Adobe Sign 고유 참여자의 식별자를 보관합니다. |
| 이름__v | 이름 | 문자열(128) | Adobe Sign 참여자의 이름을 유지합니다. |
| 주문__c | 순서 | 숫자 | Adobe 서명 계약 참가자의 주문 번호를 보관합니다. |
| 역할__c | 역할 | 문자열(30) | Adobe Sign 계약 참가자의 역할 보유 |
| 서명__c | 서명 | 개체(서명) | 서명 상위 레코드에 대한 참조를 보관합니다. |
| signature_status__c | 서명 상태 | 문자열(100) | Adobe Sign 계약 참가자의 상태 유지 |
| 사용자__c | 사용자 | 개체(사용자) | 참여자가 저장소 사용자인 경우 서명자의 사용자 레코드에 대한 참조를 보관합니다. |

![서명자 세부 정보 이미지](images/signatory-object-details.png)

### 서명 이벤트 개체 만들기  {#create-signature-event}

서명 이벤트 객체는 계약의 이벤트 관련 정보를 저장하기 위해 만들어집니다. 여기에는 다음과 같은 특정 필드에 대한 정보가 포함됩니다.

| 필드 | 레이블 | 유형 | 설명 |
| --- | --- | ---| --- | 
| acting_user_email__c | 작업 중인 사용자 전자 메일 | 문자열 | 이벤트를 발생시킨 작업을 수행한 Adobe Sign 사용자의 전자 메일을 보관합니다. |
| acting_user_name__c | 작동 사용자 이름 | 문자열 | 이벤트를 발생시킨 작업을 수행한 Adobe Sign 사용자의 이름을 유지합니다. |
| 설명__c | 설명 | 문자열 | Adobe Sign 이벤트의 설명을 보관합니다. |
| 이벤트_날짜_c | 이벤트 날짜 | 날짜 시간 | Adobe Sign 이벤트의 날짜 및 시간을 유지합니다. |
| 이벤트 유형__c | 이벤트 유형 | 문자열 | Adobe Sign 이벤트의 유형을 유지합니다. |
| 이름__v | 이름 | 문자열 | 자동 생성된 이벤트 이름 |
| 참가자_주석_c | 참가자 의견 | 문자열 | Adobe Sign 참여자의 설명이 있는 경우 |
| 참가자_전자 메일_c | 참여자 전자 메일 | 문자열 | Adobe Sign 참여자의 전자 메일 보관 |
| 참가자_역할_c | 참여자 역할 | 문자열 | Adobe Sign 참여자의 역할을 유지합니다. |
| 서명__c | 서명 | 개체(서명) | 서명 상위 레코드에 대한 참조를 보관합니다. |

![서명 이벤트 세부 정보 이미지](images/signature-event-object-details.png)

### Process Locker 개체 만들기  {#create-process-locker}

Adobe Sign 통합 프로세스를 잠그기 위해 Process Locker 개체가 만들어집니다. 사용자 지정 필드는 필요하지 않습니다.

![서명 이벤트 세부 정보 이미지](images/process-locker-details.png)

## 보안 프로필 만들기{#security-profiles}

자격 증명 모음을 통합하려면 *Adobe Sign Integration Profile*&#x200B;이라는 새 보안 프로필이 만들어지고 *Adobe Sign Admin Actions*&#x200B;에 대한 권한이 설정됩니다. Adobe Sign Integration Profile은 시스템 계정에 할당되며 Vault API를 호출할 때 통합에서 사용됩니다. 이 프로필은 다음에 대한 권한을 허용합니다.

* 자격 증명 모음 API
* 읽기, 만들기, 편집 및 삭제: 서명, 서명자, 서명 이벤트 및 Process Locker 개체

![서명 이벤트 세부 정보 이미지](images/security-profiles.png)

Vault에서 Adobe Sign 내역에 액세스해야 하는 사용자의 보안 프로파일에는 서명, 서명자 및 서명 이벤트 객체에 대한 읽기 권한이 있어야 합니다.

![서명 이벤트 세부 정보 이미지](images/set-permissions.png)

## 그룹 만들기 {#create-group}

[!DNL Vault]에 대해 Adobe Sign을 구성하려면 *Adobe Sign Admin Group*&#x200B;이라는 새 그룹이 만들어집니다. 이 그룹은 Adobe Sign 관련 필드의 문서 필드 수준 보안을 설정하는 데 사용되며 기본적으로 *Adobe Sign Integration Profile*&#x200B;을 포함해야 합니다.

![서명 이벤트 세부 정보 이미지](images/create-admin-group.png)

## 사용자 만들기 {#create-user}

Adobe Sign 통합의 저장소 시스템 계정 사용자는 다음을 수행해야 합니다.

* Adobe Sign Integration 프로필 있음
* 보안 프로필 있음
* 암호 만료를 해제하는 특정 보안 정책 있음
* Adobe Sign Admin 그룹의 멤버가 됩니다.

시스템 계정 사용자가 특정 문서 주기에 대해 Adobe Sign Admin 그룹에 속하도록 하려면 사용자 역할 설정 레코드를 만들어야 합니다.

## 응용 프로그램 역할 만들기 {#create-application-roles}

*Adobe Sign Admin Role*&#x200B;이라는 응용 프로그램 역할을 만들어야 합니다. 이 역할은 Adobe Signature에 적합한 각 문서 유형의 주기에서 정의되어야 합니다. 각 Adobe Sign 특정 주기 상태에 대해 Adobe Sign Admin 역할이 추가되고 적절한 권한으로 구성됩니다.

![응용 프로그램 역할 만들기 이미지](images/create-application-roles.png)

## 문서 필드 만들기 {#create-fields}

Adobe Sign과 통합하려면 관리자가 다음과 같은 두 개의 새 공유 문서 필드를 만들어야 합니다.

* 서명(signature__c)
* Adobe 서명 사용자 작업 허용(allow_adobe_sign_user_actions__c)

![문서 세부 정보 이미지](images/create-document-fields.png)

이러한 공유 필드는 Adobe Signature에 적합한 모든 문서 유형에 추가해야 합니다. 두 필드 모두 Adobe Sign Admin 그룹의 멤버만 해당 값을 업데이트할 수 있도록 하는 특정 보안이 있어야 합니다.

![서명 필드 세부 정보 이미지](images/signature-field-details.png)

관리자는 기존 공유 필드 *저장소 오버레이 사용 안 함(disable_vault_overlays__v)*&#x200B;을 추가하고 Adobe 서명에 적합한 모든 문서 유형에 대해 활성(Active)으로 설정해야 합니다. 선택적으로 필드에는 Adobe Sign Admin 그룹의 멤버만 해당 값을 업데이트할 수 있는 특정 보안이 있을 수 있습니다.

![adobe 서명 사용자 작업 허용 이미지](images/allow-adobe-sign-user-actions.png)

## 문서 변환 만들기 {#create-renditions}

관리자는 *Adobe Sign Rendition(adobe_sign_rendition__c)*&#x200B;이라는 새 변환 유형을 만들어야 하며, 이는 Vault 통합에서 서명된 PDF 문서를 Adobe Sign으로 업로드하는 데 사용됩니다. Adobe 서명에 적합한 각 문서 유형에 대해 Adobe 서명 변환을 선언해야 합니다.

![변환 유형 이미지](images/rendition-type.png)

![변환 유형 이미지](images/edit-details-clinical-type.png)

## 웹 작업 구성 {#web-actions}

Adobe Sign 및 Vault 통합을 사용하려면 다음 두 가지 웹 작업을 만들고 구성해야 합니다.

* **Adobe 서명** 만들기: Adobe Sign Agreement를 만들거나 표시합니다.

   유형: 문서
대상: 저장소 내에 표시
URL: <https://{integrationDomain}/adobe-sign-int/signature?docId=${Document.id}&majVer=${Document.major_version_number__v}&minVer=${Document.minor_version_number__v}&sessionId=${Session.id}&vaultId=${Vault.Id>}

* **Adobe 서명** 취소: Adobe Sign에서 기존 계약을 취소하고 문서의 상태를 초기 계약으로 되돌립니다.

   유형: 문서
대상: 저장소 내에 표시
URL: <https://{integrationDomain}/adobe-sign-int/cancel?docId=${Document.id}&majVer=${Document.major_version_number__v}&minVer=${Document.minor_version_number__v}&sessionId=${Session.id}&vaultId=${Vault.Id>}

## 문서 주기 업데이트 {#document-lifecycle}

Adobe Signature에 적합한 각 문서 유형에 대해 새 주기 역할과 상태를 추가하여 해당 문서 주기를 업데이트해야 합니다.

### 주기 역할 {#lifecycle-role}

Adobe Sign Admin 응용 프로그램 역할은 Adobe Signature에 적합한 문서에서 사용하는 모든 주기에 추가해야 합니다. 이 역할은 다음 옵션을 사용하여 만들어야 합니다.

* 동적 액세스 제어 사용
* 문서 유형 그룹만 포함하는 문서 공유 규칙

![수명 주기 관리 역할 이미지](images/document-lifecycle-admin-role.png)

### 주기 상태 {#lifecycle-states}

Adobe 서명 계약 주기의 상태는 다음과 같습니다.

* 초안
* AUTHORING 또는 DOCUMENTS_NOT_YET_PROCESSED
* OUT_FOR_SIGNATURE 또는 OUT_FOR_APPROVAL
* 서명 또는 승인
* 취소됨
* 만료됨

Vault 문서를 Adobe Sign으로 보낼 때 해당 상태는 계약의 상태와 일치해야 합니다. 이렇게 하려면 Adobe 서명에 적합한 문서에서 사용하는 모든 주기에 다음 상태를 추가합니다.

* **Adobe 서명** (검토됨) 이전: 문서를 Adobe Sign으로 보낼 수 있는 상태의 자리 표시자 이름입니다. 문서 유형에 따라 초안 상태 또는 검토됨이 될 수 있습니다. 문서 상태 레이블은 고객의 요구 사항에 따라 사용자 정의할 수 있습니다. Adobe Signature 상태가 다음 두 가지 사용자 작업을 정의하려면 먼저 다음을 수행합니다.

   * 문서 상태를 *Adobe Sign Draft* 상태로 변경하는 작업입니다. 이 사용자 작업의 이름은 모든 주기의 모든 문서 유형에 대해 동일해야 합니다. 필요한 경우 이 작업의 조건을 &quot;Adobe Sign 사용자 작업 허용(Allow Adobe Sign user actions equals eques Yes)&quot;으로 설정할 수 있습니다.
   * 웹 작업 &#39;Adobe Sign&#39;을 호출하는 작업입니다. 이 상태에는 Adobe Sign Admin 역할을 수행할 수 있는 보안이 있어야 합니다. 문서 보기, 콘텐츠 보기, 필드 편집, 관계 편집, 원본 다운로드, 보기가능 변환 관리 및 상태 변경

   ![주기 상태 1 이미지](images/lifecycle-state1.png)

* **Adobe Sign Draft에서**: 문서가 이미 Adobe Sign에 업로드되고 계약이 초안 상태에 있음을 나타내는 상태의 자리 표시자 이름입니다. 필수 상태입니다. 이 상태는 다음 다섯 가지 사용자 작업을 수행해야 합니다.

   * 문서의 상태를 *Adobe Sign Authoring* 상태로 변경하는 작업입니다. 이 사용자 작업의 이름은 모든 주기의 모든 문서 유형에 대해 동일해야 합니다. 필요한 경우 이 작업의 조건을 &quot;Adobe Sign 사용자 작업 허용(Allow Adobe Sign user actions equals eques Yes)&quot;으로 설정할 수 있습니다.
   * 문서의 상태를 *Adobe 서명 상태*&#x200B;로 변경하는 작업입니다. 이 사용자 작업의 이름은 모든 주기의 모든 문서 유형에 대해 동일해야 합니다. 필요한 경우 이 작업의 조건을 &quot;Adobe Sign 사용자 작업 허용(Allow Adobe Sign user actions equals eques Yes)&quot;으로 설정할 수 있습니다.
   * 문서의 상태를 *Adobe Sign Cancelled* 상태로 변경하는 작업입니다. 이 사용자 작업의 이름은 모든 주기의 모든 문서 유형에 대해 동일해야 합니다. 필요한 경우 이 작업의 조건을 &quot;Adobe Sign 사용자 작업 허용(Allow Adobe Sign user actions equals eques Yes)&quot;으로 설정할 수 있습니다.
   * 웹 작업 &#39;Adobe Sign&#39;을 호출하는 작업입니다.
   * 웹 작업을 &#39;Adobe 서명 취소&#39;라고 부르는 작업입니다. 이 상태에는 Adobe Sign Admin 역할을 수행할 수 있는 보안이 있어야 합니다. 문서 보기, 콘텐츠 보기, 필드 편집, 관계 편집, 원본 다운로드, 보기가능 변환 관리 및 상태 변경

   ![주기 상태 2 이미지](images/lifecycle-state2.png)

* **Adobe 서명 제작에서**: 문서가 이미 Adobe Sign에 업로드되고 해당 계약이 AUTHORING 또는 DOCUMENTS_NOT_YET_PROCESSED 상태임을 나타내는 상태의 자리 표시자 이름입니다. 필수 상태입니다. 이 상태에는 다음 네 가지 사용자 작업이 정의되어 있어야 합니다.

   * 문서의 상태를 Adobe 서명 취소 상태로 변경하는 작업입니다. 이 사용자 작업의 이름은 주기에 관계없이 모든 문서 유형에 대해 동일해야 합니다. 필요한 경우 이 작업의 조건을 &quot;Adobe Sign 사용자 작업 허용(Allow Adobe Sign user actions equals eques Yes)&quot;으로 설정할 수 있습니다.
   * 문서의 상태를 Adobe 서명 상태로 변경하는 작업입니다. 이 사용자 작업의 이름은 주기에 관계없이 모든 문서 유형에 대해 동일해야 합니다. 필요한 경우 이 작업의 조건을 &quot;Adobe Sign 사용자 작업 허용(Allow Adobe Sign user actions equals eques Yes)&quot;으로 설정할 수 있습니다.
   * 웹 작업 &#39;Adobe Sign&#39;을 호출하는 동작
   * 웹 작업을 &#39;Adobe 서명 취소&#39;라고 부르는 작업입니다. 이 상태에는 Adobe Sign Admin 역할을 수행할 수 있는 보안이 있어야 합니다. 문서 보기, 콘텐츠 보기, 필드 편집, 관계 편집, 원본 다운로드, 보기가능 변환 관리 및 상태 변경

   ![주기 상태 3 이미지](images/lifecycle-state3.png)

* **Adobe 서명에서**: 문서가 Adobe Sign에 업로드되고 해당 계약이 이미 참여자에게 보내졌음을 나타내는 상태(OUT_FOR_SIGNATURE 또는 OUT_FOR_APPROVAL 상태)의 자리 표시자 이름입니다. 필수 상태입니다. 이 상태에는 다음 다섯 가지 사용자 작업이 정의되어 있어야 합니다.

   * 문서의 상태를 Adobe 서명 취소 상태로 변경하는 작업입니다. 이 작업의 대상 상태는 고객 요구 사항이 무엇이든 될 수 있으며 다른 유형에 따라 다를 수 있습니다. 이 사용자 작업의 이름은 주기에 관계없이 모든 문서 유형에 대해 동일해야 합니다. 필요한 경우 이 작업의 조건을 &quot;Adobe Sign 사용자 작업 허용(Allow Adobe Sign user actions equals eques Yes)&quot;으로 설정할 수 있습니다.
   * 문서의 상태를 Adobe [서명 거부] 상태로 변경하는 작업입니다. 이 작업의 대상 상태는 고객 요구 사항이 무엇이든 될 수 있으며 다른 유형에 따라 다를 수 있습니다. 이 사용자 작업의 이름은 주기에 관계없이 모든 문서 유형에 대해 동일해야 합니다. 필요한 경우 이 작업의 조건을 &quot;Adobe Sign 사용자 작업 허용(Allow Adobe Sign user actions equals eques Yes)&quot;으로 설정할 수 있습니다.
   * 문서의 상태를 Adobe 서명 상태로 변경하는 작업입니다. 이 작업의 대상 상태는 고객 요구 사항이 무엇이든 될 수 있으며 다른 유형에 따라 다를 수 있습니다. 그러나 이 사용자 작업의 이름은 주기에 관계없이 모든 문서 유형에 대해 동일해야 합니다. 필요한 경우 이 작업의 조건을 &quot;Adobe Sign 사용자 작업 허용(Allow Adobe Sign user actions equals eques Yes)&quot;으로 설정할 수 있습니다.
   * 웹 작업 *Adobe Sign*&#x200B;을 호출하는 작업입니다.
   * Web Action *Adobe Sign* 취소를 호출하는 작업입니다. 이 상태에는 Adobe Sign Admin 역할을 수행할 수 있는 보안이 있어야 합니다. 문서 보기, 콘텐츠 보기, 필드 편집, 관계 편집, 원본 다운로드, 보기가능 변환 관리 및 상태 변경

   ![주기 상태 4 이미지](images/lifecycle-state4.png)

* **Adobe 서명(승인됨)**: 문서가 Adobe Sign으로 업로드되고 계약이 완료되었음을 나타내는 상태(SIGNED 또는 APPROVED 상태)의 자리 표시자 이름입니다. 필수 상태이며 승인됨과 같은 기존 주기 상태가 될 수 있습니다.
이 상태에서는 사용자 작업이 필요하지 않습니다. 이 상태에는 Adobe Sign Admin 역할을 수행할 수 있는 보안이 있어야 합니다. 문서 보기, 컨텐트 보기 및 필드 편집

다음 다이어그램은 &#39;Adobe 서명 전&#39; 상태가 [초안]인 Adobe 서명 동의와 저장소 문서 상태 간의 매핑을 보여 줍니다.

![Adobe Sign Vault 매핑 이미지](images/sign-vault-mappings.png)

## 문서 유형 그룹 및 사용자 역할 설정 만들기  {#document-type-group-user-role}

### 문서 유형 그룹 만들기 {#create-document-type-group}

관리자는 &quot;Adobe 서명 문서&quot;라는 새 문서 유형 그룹 레코드를 만들어야 합니다. 이 문서 유형 그룹은 Adobe 서명 프로세스에 적합한 모든 문서 분류에 추가됩니다. 문서 유형 그룹 속성은 유형에서 하위 유형으로 상속되거나 하위 유형에서 분류 레벨로 상속되지 않으므로 Adobe Sign에 적합한 각 문서의 분류에 대해 설정해야 합니다.

![문서 유형의 이미지](images/document-type.png)

### 사용자 역할 만들기 설정 {#create-user-role-setup}

주기가 올바르게 구성되면 시스템은 Adobe Sign 프로세스에 적합한 모든 문서에 대해 DAC에서 Adobe Sign Admin 사용자를 추가해야 합니다. 이 작업은 다음을 지정하는 적절한 사용자 역할 설정 레코드를 만들어 수행됩니다.

* 문서 유형 그룹을 &#39;Adobe 서명 문서&#39;로,
* &#39;Adobe Sign Admin Role&#39;의 응용 프로그램 역할
* 통합 사용자입니다.

![사용자 역할 설정 이미지](images/user-role-setup.png)

>[!NOTE]
>
>사용자 역할 설정 개체에 문서 유형 그룹 개체를 참조하는 필드가 없으면 이 필드를 추가해야 합니다.

## 미들웨어를 사용하여 [!DNL Veeva Vault]을(를) Adobe Sign에 연결 {#connect-middleware}

[!DNL Veeva Vault] 및 Adobe Sign Admin 계정에 대한 설정을 완료한 후 관리자는 미들웨어를 사용하여 두 계정 간에 접속을 생성해야 합니다. [!DNL Veeva Vault] 및 Adobe Sign accountnt 연결은 Adobe Sign Identity에서 시작한 다음 Veeva Vault ID를 저장하는 데 사용됩니다.Adobe Sign 계정 관리자는 미들웨어를 사용하여 [!DNL Veeva Vault]을 Adobe Sign에 연결하려면 다음 단계를 따라야 합니다.

1. [홈 페이지](https://static.adobesigncdn.com/veevavaultintsvc/index.html)의 Adobe Sign으로 이동합니다. [!DNL Veeva Vault] 
1. 오른쪽 위에서 **[!UICONTROL 로그인]**&#x200B;을 선택합니다.

   ![미들웨어 로그인 이미지](images/middleware_login.png)

1. 열리는 Adobe Sign 로그인 페이지에서 계정 관리자 전자 메일 및 암호를 제공한 다음 **[!UICONTROL Sing in]**&#x200B;을 선택합니다.

   ![이미지](images/middleware-signin.png)

   로그인에 성공하면 아래와 같이 연관된 전자 메일 ID와 설정 탭이 표시됩니다.

   ![이미지](images/middleware_settings.png)

1. **[!UICONTROL 설정]** 탭을 선택합니다.

   설정 페이지에는 사용 가능한 연결이 표시되며, 아래와 같이 첫 번째 연결 설정의 경우 아무 것도 표시되지 않습니다.

   ![이미지](images/middleware_newconnection.png)

1. **[!UICONTROL 연결 추가]**&#x200B;를 선택하여 새 연결을 추가합니다.

1. 열리는 연결 추가 대화 상자에서 [!DNL Veeva Vault] 자격 증명을 포함하여 필요한 세부 정보를 제공합니다.

   Adobe Sign Credentials는 초기 Adobe Sign 로그인에서 자동으로 채워집니다.

   ![이미지](images/middleware_addconnection.png)

1. **[!UICONTROL Validate]**&#x200B;를 선택하여 계정 세부 정보를 확인합니다.

   유효성 검사가 성공하면 아래와 같이 &#39;사용자가 성공적으로 검증됨&#39; 알림이 표시됩니다.

   ![이미지](images/middleware_validated.png)

1. 사용을 특정 Adobe Sign Group으로 제한하려면 **[!UICONTROL 그룹]** 드롭다운 목록을 확장하고 사용 가능한 그룹 중 하나를 선택합니다.

   ![이미지](images/middleware_group.png)

1. **[!UICONTROL Save]**&#x200B;를 선택하여 새 연결을 저장합니다.

   새 연결은 [!DNL Veeva Vault]과(와) Adobe Sign 간의 성공적인 통합을 보여주는 설정 탭에 나타납니다.

   ![이미지](images/middleware_setup.png)

## 패키지 배포 수명 주기 {#deployment-lifecycle}

### 일반 배포 수명 주기 {#general-deployment}

**1단계.** &#39;Adobe Sign Admin Role&#39;이라는 새 응용 프로그램 역할을 만듭니다.

**2단계.** &#39;Adobe Sign Document&#39;라는 새 문서 유형 그룹을 만듭니다.

**3단계.** 패키지를 배포합니다.

**4단계** &#39;Adobe Sign Admin Group&#39;이라는 새 사용자 관리 그룹을 만듭니다.

**5단계** 보안 프로필 &quot;Adobe Sign Integration Profile&quot;을 사용하여 통합 사용자 프로필을 만들고 Adobe Sign Admin 그룹에 할당합니다.

**6단계** Vault에서 Adobe 로그인 기록에 액세스해야 하는 사용자를 위해 모든 보안 프로파일에 대한 읽기 권한을 서명, 서명자 및 서명 이벤트 객체에 할당합니다.

**7단계** Adobe Signature에 적합한 각 문서 유형의 주기에서 Adobe Sign Admin 역할을 정의합니다. 각 Adobe Sign 특정 주기 상태에 대해 이 역할이 추가되고 적절한 권한으로 구성됩니다.

**8단계** Adobe 서명에 적합한 각 문서 유형에 대해 Adobe 서명 변환을 선언합니다.

**9단계** Adobe Signature에 적합한 각 문서 유형에 대해 새 주기 역할과 상태를 추가하여 해당 문서 주기를 업데이트합니다.

**10단계** Adobe Sign 프로세스에 적합한 모든 문서 분류에 대해 &#39;Adobe Sign Document&#39;라는 문서 유형 그룹을 추가합니다.

**11단계** 모든 구성이 완료되면 Adobe Sign 프로세스에 적합한 모든 문서에 대해 DAC에서 Adobe Sign Admin 사용자를 추가해야 합니다. 이 작업은 문서 유형 그룹을 &#39;Adobe Sign Document&#39;, 응용 프로그램 역할을 &#39;Adobe Sign Admin Role&#39; 및 통합 사용자로 지정하는 적절한 사용자 역할 설정 레코드를 만들어 수행됩니다.

### 특정 배포 수명 주기 {#specific-deployment}

**1단계.** &#39;Adobe Sign Admin Role&#39;이라는 새 응용 프로그램 역할을 만듭니다.

**2단계.** &#39;Adobe Sign Document&#39;라는 새 문서 유형 그룹을 만듭니다.

**3단계.** 패키지를 배포합니다.

**4단계** &#39;Adobe Sign Admin Group&#39;이라는 새 사용자 관리 그룹을 만듭니다.

**5단계** &#39;Adobe Sign Integration Profile&#39;이라는 보안 프로필을 사용하여 하나의 통합 사용자 프로필을 만들고 Adobe Sign Admin 그룹에 할당합니다.
