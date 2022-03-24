---
title: Workday 빠른 시작 안내서
description: Workday 환경에서 Adobe Sign을 사용하려는 고객을 위한 빠른 시작 안내서입니다.
uuid: 10bf8ee8-9075-44d1-a836-e454950e2d9a
products: Adobe Sign
content-type: reference
discoiquuid: 13135c88-4c39-4707-b7ba-63ff94769258
locnotes: All languages; screenshots to follow what's there already (seems there is a mix within a given language version of the article)
type: Documentation
solution: Acrobat Sign, Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 8b6fa8b4-e240-4ebe-ae2a-8807d75a6c69
source-git-commit: b326a9afa2c16333d390cac3b30a2c7c741a4360
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 23%

---

# [!DNL Workday]빠른 시작 안내서 {#workday-quick-start-guide}

[**Adobe Sign 지원 문의**](https://www.adobe.com/go/adobesign-support-center)

## 개요 {#overview}

이 문서는 [!DNL Workday] 관리자는 사용자 정의 방법을 이해합니다. [!DNL Workday] 전자 서명 획득을 위한 Adobe Sign을 포함하는 비즈니스 프로세스. Adobe Sign 사용 방법 [!DNL Workday]를 만들고 수정하는 방법을 알고 있어야 합니다. [!DNL Workday] 다음과 같은 항목:

* [!UICONTROL 비즈니스 프로세스 프레임워크]
* 테넌트 설정 및 구성
* 보고 및 [!DNL Workday] Studio 통합

##  내 Adobe Sign 액세스[!DNL Workday] {#access-adobe-sign}

[!UICONTROL Adobe Sign 전자 서명 기능] 다음과 같이 표시됩니다. [!UICONTROL 문서 검토 단계] 내부 작업 [!UICONTROL 비즈니스 프로세스 프레임워크(BPF)] 및 을 문서 배포 작업으로 추가합니다.

## [!UICONTROL 문서 검토 단계] {#review-document-step}

Adobe Sign [!DNL Workday] 을(를) 통해 [!UICONTROL 문서 검토 단계] 400개 이상의 비즈니스 프로세스에 [!DNL Workday], 포함 [!UICONTROL 혜택], [!UICONTROL 문서 및 작업 배포], [!UICONTROL 보상 제안]등의 세부 정보가 포함되어 있습니다.

자세한 내용은 [[!DNL Workday] 커뮤니티 문서 [!UICONTROL 문서 검토 단계]](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg).

1:1 관계가 있습니다 [!UICONTROL [!UICONTROL 문서 검토 단계]s] 및 Adobe Sign으로 청구 가능한 트랜잭션 여러 문서를 단일 문서 내에서 결합할 수 있습니다 [!UICONTROL 문서 검토 단계] 서명을 위한 단일 패키지로 표시됩니다.

**참고**: 단일 *동적* 특정 문서에서 참조할 수 있습니다. [!UICONTROL 문서 검토 단계].

기능 정의 [!UICONTROL 문서 검토 단계]:

1. 삽입 [!UICONTROL 문서 검토 단계].
1. 다음에 대해 조치를 취할 수 있는 그룹(역할) 지정 [!UICONTROL 문서 검토 단계].

![비즈니스 프로세스 단계](images/insert-review-doc-steptornm-575.png)

를 구성하려면 [!UICONTROL 문서 검토 단계]:

1. 다음을 지정합니다. *[!UICONTROL eSignature 통합 유형]* 만큼 *[!UICONTROL Adobe 전자 서명]*.

1. 서명 격자에 행 추가.

   * 서명 격자는 서명을 받으러 문서가 라우팅되는 순차적인 순서를 지정합니다. 각 행에 한 개 이상의 역할을 지정할 수 있고 각 행이 서명 프로세스의 한 단계를 나타냅니다..
   * 특정 단계 내에서 역할의 모든 구성원에게 서명 이벤트가 보류 중임을 알립니다.
   * 역할의 한 사람이 서명하면 행 단계가 완료되고 문서가 다음 행 단계로 이동합니다.
   * 모든 행에 서명된 경우 [!UICONTROL 문서 검토 단계] 이(가) 완료되었습니다.

1. 서명받을 문서를 지정합니다. 문서가 [!UICONTROL BP 제공]문서 생성 단계에서 사용할 수 있습니다. 그렇지 않은 경우 기존 문서 또는 보고서를 선택하십시오.

1. 필요한 만큼 문서가 생길 때까지 3단계를 반복합니다..

   ![문서 검토 단계 구성](images/configure-rd-stepsmaller-575.png)

1. 선택적으로 &#39;서명 거절&#39; 동작을 캡처하려면 &#39;사용자 리디렉션&#39;을 추가합니다. 사용자가 거절하면 [!DNL Workday] 검토를 위해 문서를 구성된 보안 그룹으로 리디렉션합니다.

의 관련 작업 메뉴에서 [!UICONTROL 문서 검토 단계], 선택 **[!UICONTROL 비즈니스 프로세스]** > **[!UICONTROL 리디렉션 유지]**. 다음 중 하나를 선택합니다.

* **[!UICONTROL 뒤로 보내기]**: 보안 그룹 구성원이 비즈니스 프로세스에서 한 단계를 이전 단계로 되돌려 보낼 수 있도록 합니다. 비즈니스 프로세스가 해당 단계에서 다시 시작됩니다.
* **[!UICONTROL 다음 단계로 이동]**: 보안 그룹 구성원이 비즈니스 프로세스에서 한 단계를 다음 단계로 보낼 수 있도록 합니다.
* **[!UICONTROL 보안 그룹]**: 비즈니스 프로세스 플로우에서 단계를 리디렉션하려면 이 프롬프트에 표시되는 보안 그룹은 리디렉션 섹션의 비즈니스 프로세스 보안 정책에서 선택됩니다.

## 비즈니스 프로세스 단계 참고 사항 {#business-process-step-notes}

[!UICONTROL 비즈니스 프로세스 프레임워크] 강력한 성능; 단, 다음 사항을 확인해야 합니다.

* 모든 비즈니스 프로세스에는 이상적으로 비즈니스 프로세스의 마지막에 있는 완료 단계가 있어야 합니다.

* 완료 단계는 검색 아이콘의 관련 동작 메뉴에서 설정됩니다. 이는 BP를 &quot;보고&quot; 있는 동안에만 가능하며, BP를 &quot;편집&quot; 하는 동안에는 가능하지 않다.

* 비즈니스 프로세스의 모든 단계는 순차적으로 실행됩니다.

   순서 값을 변경하여 단계의 순서를 변경할 수 있습니다. 예를 들어 항목 &quot;c&quot;와 &quot;d&quot; 사이에 단계를 삽입하려면 새 항목을 &quot;ca&quot;로 지정합니다.

### 예: 제안 {#example-offer}

Offer BP는 [!UICONTROL 직무 지원 동적 BP] 제공 BP를 실행하도록 구성해야 합니다. 작업 응용 프로그램 상태가 &quot;[!UICONTROL 혜택]&quot; 또는 &quot;[!UICONTROL 제안 만들기]&quot;.

아래 예에서는 [!UICONTROL 문서 검토 단계] 는 북미와 일본에 모두 동적 문서 단계를 사용하고 있습니다.

![[!DNL Workday] 비즈니스 프로세스의 예](images/bp-for-offersmaller-575.png)

이 BP는 다음 작업을 수행합니다.

* BP의 개시자에게 후보자에 대한 보상을 제안하도록 요청한다(단계 b).
* 단계 조건을 사용하여 현재 국가가 일본이 아닌지 테스트합니다.

   true이면 영어 문서를 사용하는 &quot;ba&quot; 단계가 실행됩니다.

   false인 경우 일본어 문서를 사용하는 &quot;bb&quot; 단계를 실행합니다.

* 서명 프로세스를 [!UICONTROL 문서 검토 단계] &quot;bc&quot;
* 필수 완료 단계 &quot;d&quot;에서 오퍼를 제기할 결정 지점을 정의합니다.

“ba”단계에서 생성되는 동적 문서를 [!UICONTROL 구인 공고(Offer Letter)]라고 하며 [!UICONTROL 긴급 구인(Rapid Offer)]이라고 적힌 텍스트 블록이 1개 포함되어 있습니다. 필요에 따라 머리글, 인사말, 보상, 스톡, 마감, 용어 등과 같은 여러 텍스트 블록을 추가할 수 있습니다.

![[!DNL Workday] 문서 페이지 보기](images/offer-letter-575.png)

아래 동적 제안서는 [!DNL Workday] 리치 텍스트 편집기입니다. 에서 강조된 항목 *회색* 이 [!DNL Workday] 컨텍스트 데이터를 참조하는 개체를 제공했습니다.

{{brackets}} 안의 항목은 [Adobe 텍스트 태그](https://adobe.com/go/adobesign_text_tag_guide_kr)입니다.

![예제 동적 양식](images/script.png)

에 [!UICONTROL 문서 검토 단계]동적 문서는 이전 단계에서 참조되며 두 개의 서명 그룹을 통해 순차적 서명 프로세스를 정의합니다.

아래에 설명된 동작은 동적으로 생성된 문서를 먼저 고용 관리자에게 라우팅한 다음, 지원자에게 라우팅합니다.

![[!DNL Workday] 정의된 서명 그룹](images/configure-rd-stepsmaller-575.png)

### 예: 문서 배포 {#example-distribute-documents}

도입 위치 [!DNL Workday] 30의 경우 문서 또는 작업 대량 배포 작업을 사용하여 하나의 문서를 대규모(2만 미만) 개별 서명자에게 보낼 수 있습니다. 이 기능은 문서당 단일 서명으로 제한됩니다. 배포 생성은 &#39;[!UICONTROL 문서 또는 작업 배포 만들기]&#39; 작업을 수행할 수 있습니다.

예: 직원 지분 선택 양식을 [!UICONTROL 글로벌 모던 서비스]. 원하는 경우 개별 관리자에게 추가로 필터링할 수 있습니다.

또한 **문서 또는 작업 배포 보기** 배포 진행 상태를 추적하는 보고서입니다.

![](images/create-distributedocumentsortasks.png)

### 예: 보고 {#example-reporting}

[!DNL Workday] 다양한 보고 인프라를 갖추고 있습니다. Adobe Sign 프로세스의 세부 사항을 보려면 *문서 검토 이벤트*&#x200B;의 요소를 점검하십시오.

다음은 모든 BP에 걸쳐 Adobe Sign 트랜잭션과 그 상태를 알아보기 위해 실행할 수 있는 간단한 사용자 지정 보고서입니다.

![[!DNL Workday] 사용자 지정 보고서의 예](images/review-document-eventsmaller-575.png)

아래 보고서는 구현 임차인 내 구인, 입사 및 보상 제안 BP를 보고 생성되었습니다.

확인 가능한 항목:

* 서명을 받으러 발송된 문서
* 연결된 BP 단계
* 서명 대기 중인 다음 사람

![[!DNL Workday]세 개의 개체를 사용하는 보고서의 예](images/workday-reportsmaller-575.png)

## 서명된 문서 {#signed-documents}

추가 [!DNL Workday] 서명 주기는 Adobe Sign의 모든 전자 메일 알림을 표시하지 않습니다. 사용자는 자신의 작업 내에서 보류 중인 작업에 대해 [!DNL Workday] 받은 편지함입니다.

모든 서명 그룹에서 문서에 서명을 받으면 서명된 문서의 사본이 전자 메일을 통해 서명 그룹의 모든 구성원에게 배포됩니다.

이 동작을 억제하려면 [!UICONTROL Adobe Sign 성공 관리자] 또는 [Adobe Sign 지원팀](https://adobe.com/go/adobesign-support-center).

이내 [!DNL Workday]전체 프로세스 레코드에서 서명된 문서에 액세스할 수 있습니다. 다음과 같은 항목을 찾을 수 있습니다.

* 작업자 프로파일의 작업자 문서
* 후보 프로필의 후보 문서(제안서).

아래 이미지는 후보 Chris Foxx에 대한 서명된 오퍼 레터를 보여줍니다.

![예 [!DNL Workday] 오퍼 레터](images/offer.png)

## 지원 {#support}

### [!DNL Workday] 지원 {#workday-support}

[!DNL Workday] 통합 소유자이며 통합 범위, 기능 요청 또는 통합의 일상적인 기능에 대한 질문에 대한 첫 번째 연락처여야 합니다.

추가 [!DNL Workday] 커뮤니티에는 통합 문제를 해결하고 문서를 생성하는 방법에 대한 몇 가지 유용한 기사가 있습니다.

* [전자 서명 통합 문제 해결](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/zhA~hYllD3Hv1wu0CvHH_g)
* [문서 검토 단계](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)
* [동적 문서 생성](https://community.workday.com/node/176443)
* [구인 문서 생성 구성 팁](https://community.workday.com/node/183242)

### Adobe Sign 지원 {#adobe-sign-support}

Adobe Sign은 통합 파트너로서, 통합 과정에서 서명을 받지 못하거나 대기 중인 서명의 알림에 실패하는 경우에 문의해야 합니다.

Adobe Sign 고객은 고객 성공 관리자에게 지원을 요청해야 합니다. 또는 [!UICONTROL Adobe 기술 지원] 전화로 연결할 수 있습니다. 1-866-318-4100, 제품 목록을 기다린 후 다음을 입력합니다. 4와 2를 차례로 선택합니다(프롬프트에 따라).

* [문서에 Adobe 텍스트 태그 추가하기](https://www.adobe.com/go/adobesign_text_tag_guide)

<!--
[Download PDF](images/adobe-sign-for-workday-quick-start-guide-2016.pdf)
-->
