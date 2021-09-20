---
title: Workday 평가판 설치
description: Adobe Sign의 평가판 계정 Workday 설치 가이드
uuid: 0c51f329-b7c1-44a2-88a3-670be7673747
products: Adobe Sign
topic-tags: EchoSign/Integrations
content-type: reference
discoiquuid: 63ed2d5b-9d82-4f87-97e1-2dde23501e89
locnotes: All languages; screenshots for Tier 1 and 2 only (see the currently published localized page for guidance)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: beafe6c0-262f-4f5b-9315-a023a4eef4a2
source-git-commit: 78d6cafa720b41bd638c2ef723b2d4a2def19cd5
workflow-type: tm+mt
source-wordcount: '998'
ht-degree: 29%

---

# [!DNL Workday] 평가판 설치{#workday-trial-installation}

## 개요 {#overview}

이 문서는 [!DNL Workday] 고객이 Adobe Sign을 사용하여 평가판 계정을 활성화한 다음 [!DNL Workday] 테넌트에 통합하는 방법을 배울 수 있도록 설계되었습니다. [!DNL Workday] 내에서 Adobe Sign을 사용하려면 다음과 같은 [!DNL Workday] 항목을 만들고 수정하는 방법을 알아야 합니다.

* 비즈니스 프로세스 프레임워크
* 테넌트 설정 및 구성
* 보고 및 [!DNL Workday] Studio 통합

**참고**: 기존 Adobe Sign 계정이 있는 경우 평가판을 시작할 필요가 없습니다. 클라이언트 성공 관리자에게 문의하여 [!DNL Workday] 통합을 요청할 수 있습니다.

통합을 완료하는 고수준의 단계는 다음과 같습니다.

* Adobe Sign 시험판 계정의 활성화
* Adobe Sign에서 통합 키 생성
* [!DNL Workday] 테넌트에 통합 키 설치

## Adobe Sign 평가판 계정 활성화 {#activate-sign-trial-account}

Adobe Sign의 30일 평가판을 요청하려면 [등록 양식](https://land.echosign.com/esign-trial-workday-registration.html)을 작성해야 합니다.

**참고**: 임시 전자 메일이 아닌 평가판을 만들려면 유효한 기능 전자 메일 주소를 사용하는 것이 좋습니다. 계정을 확인하려면 이 전자 메일에 액세스해야 하므로 주소가 유효해야 합니다.

![시험판 요청 양식](images/trial-land.png)

Adobe Sign on-boarding 전문가는 업무일 1일 이내에 [!DNL Workday]에 대한 계정을 Adobe Sign에서 제공합니다. 완료되면 아래와 같이 확인 이메일을 받게 됩니다.

![Adobe Sign 시작 이메일](images/welcome-email-2020.png)

전자 메일의 지시에 따라 계정을 초기화하고 Adobe Sign [!UICONTROL Home] 페이지에 액세스합니다.

![Adobe Sign 대시보드](images/classic-home.png)

## 통합 키 생성 {#generate-an-integration-key}

새 설치의 경우 Adobe Sign에서 통합 키를 생성한 다음 [!DNL Workday]에 입력해야 합니다. 이 키는 서로 신뢰하고 내용을 공유하기 위해 Adobe Sign 및 [!DNL Workday] 환경을 인증합니다.

Adobe Sign에서 통합 키 생성하기:

1. Adobe Sign 관리자에 로그인합니다..
1. **[!UICONTROL **Account]** > **[!UICONTROL Personal Preferences]** > **[!UICONTROL Access Tokens*]**&#x200B;로 이동합니다.
1. 창 오른쪽에 있는 **원 안의 더하기 아이콘**&#x200B;을 클릭합니다.

   [!UICONTROL 통합 키 만들기] 인터페이스를 엽니다.

   ![액세스 토큰 페이지로의 이동 이미지](images/navigate-to-group-accesstokens.png)

1. [!DNL Workday]과 같이 키에 대한 직관적인 이름을 제공하십시오.

   통합 키에 다음 요소가 활성화되어 있어야 합니다.

   * agreement_read
   * agreement_write
   * agreement_send
   * widget_read
   * library_read

   ![통합 키 만들기 패널](images/create-integration-key-575.png)

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

   [!UICONTROL 액세스 토큰] 페이지가 나타나고 해당 계정으로 만들어진 키가 표시됩니다.

1. [!DNL Workday]에 대해 만든 키 정의를 클릭합니다.

   [!UICONTROL 통합 키] 링크가 정의 맨 위에 표시됩니다.

1. **[!UICONTROL 통합 키]** 링크를 클릭합니다.

   통합 키를 표시합니다.

   ![통합 키 링크](images/integration-key.png)

1. 이 키를 복사하고 다음 단계를 위해 안전한 곳에 저장합니다.
1. **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

   ![통합 키 패널](images/copy-the-key-575.png)

## [!DNL Workday] 테넌트 구성 {#configuring-the-workday-tenant}

### 통합 키 설치 {#install-the-integration-key}

[!DNL Workday] 테넌트에 통합 키를 설치하면 Adobe Sign과의 트러스트 관계가 설정됩니다. 이러한 관계가 유지되면 모든 비즈니스 프로세스에서 서명 프로세스를 가능하게 하는 [!UICONTROL 문서 단계 검토]를 추가할 수 있습니다.

**참고**[!DNL Workday]: Adobe Sign은 환경 여기저기에 “Adobe Document Cloud”로 표시됩니다.

통합 키 설치 방법:

1. 계정 관리자로 [!DNL Workday]에 로그인합니다.
1. **[!UICONTROL 테넌트 설정 편집 - 비즈니스 프로세스]** 페이지를 검색하고 엽니다.

1. 다음 네 필드에 대한 정보를 제공합니다.

   * **[!UICONTROL Adobe Document 클라우드 승인]**: 통합에 대한 고정 텍스트 승인

   * **[!UICONTROL Adobe Document Cloud API 키]**: 통합 키가 설치된 위치

   * **[!UICONTROL Adobe Document Cloud Sender 전자 메일 주소]**: Adobe Sign에서 그룹 수준 관리자의 전자 메일 주소

   * **[!UICONTROL 문서가 취소될 때 eSignature 대기 중인 문서 제거]**: 에서 문서가 취소된 경우 서명 주기에서 문서를 제거하는 선택적 구성입니다  [!DNL Workday].

   ![Adobe Sign 통합 키 필드](images/bp-filled-torn2-575.png)

1. 다음으로 설치를 완료합니다.

   1. Integration 키를 [!UICONTROL Adobe Sign API Integration Key] 필드에 붙여넣습니다.
   1. [!UICONTROL Adobe Document Cloud Sender Email Address] 필드에 Adobe Sign 관리자의 전자 메일 주소를 입력합니다.
   1. **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

   ![통합 키 필드와 키 소유자 이메일 필드](images/bp-filled-small.png)

이제 [!UICONTROL 문서 단계 검토]를 추가하고 **[!UICONTROL eSign by Adobe]**&#x200B;을 eSignature 유형으로 사용하도록 구성하여 모든 비즈니스 프로세스에 Adobe 서명 기능을 추가할 수 있습니다.

### 검토 문서 단계 구성 {#configure-the-review-document-step}

문서 검토 단계의 문서는 정적 문서일 수 있습니다. 동일한 업무 프로세스 내에서 문서 생성 단계에 의해 생성된 문서 또는 [!DNL Workday] 보고서 디자이너로 만든 서식 있는 보고서입니다. Adobe 서명에 따른 구성요소의 모양 및 위치를 제어하는 [Adobe 텍스트 태그](https://adobe.com/go/adobesign_text_tag_guide_kr)를 사용하여 이러한 모든 종류의 문서를 보완할 수 있습니다. 비즈니스 프로세스 정의 내에 문서 원본이 지정되어야 합니다. 업무 프로세스가 실행되는 동안에는 임시 문서를 업로드할 수 없습니다.

문서 검토 단계와 함께 Adobe Sign을 사용하는 것은 서명자 그룹을 직렬화할 수 있는 기능입니다. 서명자 그룹을 사용하면 순번에 로그인하는 역할 기반 그룹을 지정할 수 있습니다. Adobe Sign에서는 병렬 서명 그룹을 지원하지 않습니다.

문서 검토 단계를 구성하는 데 도움이 필요하면 [빠른 시작 안내서](https://adobe.com//go/adobesign_workday_quick_start){target=&quot;_blank&quot;}를 참조하십시오.

## 지원 {#support}

### [!DNL Workday] 지원 {#workday-support}

[!DNL Workday] 통합 소유자이며 통합 범위, 기능 요청 또는 통합의 일상적인 기능에서 발생하는 문제에 대한 질문을 받을 수 있는 첫 번째 담당자여야 합니다.

[!DNL Workday] 커뮤니티에는 통합 문제를 해결하고 문서를 생성하는 방법에 대한 몇 가지 좋은 기사가 있습니다.

* [전자 서명 통합 문제 해결](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [문서 검토 단계](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [동적 문서 생성](https://community.workday.com/node/176443)

* [구인 문서 생성 구성 팁](https://community.workday.com/node/183242)

### Adobe 서명 지원 {#adobe-sign-support}

Adobe Sign은 통합 파트너로서, 통합 과정에서 서명을 받지 못하거나 대기 중인 서명의 알림에 실패하는 경우에 문의해야 합니다.

Adobe Sign 고객은 담당 고객 성공 관리자(CSM)에게 지원을 요청해야 합니다. 또는 전화로 Adobe 기술 지원을 받을 수 있습니다. 1-866-318-4100 제품 목록을 기다린 다음 다음을 입력합니다. 4를 누르고 2를 누릅니다.

* [문서에 Adobe 텍스트 태그 추가하기](https://adobe.com/go/adobesign_text_tag_guide)

* [문서 구성 및 예제 검토](https://www.adobe.com//go/adobesign_workday_quick_start)

[**Adobe Sign 지원 문의**](https://adobe.com/go/adobesign-support-center_kr)
