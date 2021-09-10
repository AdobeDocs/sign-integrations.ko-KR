---
title: Workday 빠른 시작 안내서
description: Adobe Sign을 사용하려는 고객을 위한 빠른 시작 안내서입니다.
uuid: 10bf8ee8-9075-44d1-a836-e454950e2d9a
products: Adobe Sign
content-type: reference
discoiquuid: 13135c88-4c39-4707-b7ba-63ff94769258
locnotes: All languages; screenshots to follow what's there already (seems there is a mix within a given language version of the article)
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
exl-id: 8b6fa8b4-e240-4ebe-ae2a-8807d75a6c69
source-git-commit: d462ccf41fa5483cfa02f5eaf154c23f26157a1e
workflow-type: tm+mt
source-wordcount: '1352'
ht-degree: 30%

---

# [!DNL Workday]빠른 시작 안내서 {#workday-quick-start-guide}

[**Adobe Sign 지원 문의**](https://adobe.com/go/adobesign-support-center_kr)

## 개요 {#overview}

이 문서는 [!DNL Workday] 관리자가 e-signature를 얻기 위해 Adobe Sign을 포함하도록 [!DNL Workday] 비즈니스 프로세스를 사용자 지정하는 방법을 이해하도록 설계되었습니다. [!DNL Workday] 내에서 Adobe Sign을 사용하려면 다음과 같은 [!DNL Workday] 항목을 만들고 수정하는 방법을 알아야 합니다.

* 비즈니스 프로세스 프레임워크
* 테넌트 설정 및 구성
* 보고 및 [!DNL Workday] Studio 통합

##  내 Adobe Sign 액세스[!DNL Workday] {#access-adobe-sign}

Adobe 서명 전자 서명 기능은 BPF(Business Process Framework)에서 [!UICONTROL 문서 단계 검토] 작업으로 표시되고 문서 배포 작업으로 표시됩니다.

## [!UICONTROL 문서 검토 단계] {#review-document-step}

[!DNL Workday]에 대한 Adobe Sign은 [!UICONTROL 문서 단계 검토]를 통해 공개되며, 제안, 문서 및 작업 배포, 보상 제안 등을 포함하여 [!DNL Workday] 내 400개 이상의 비즈니스 프로세스에 추가할 수 있습니다.

[!UICONTROL Review Document Step]](https://doc.workday.com/#/reader/3DMnG~27o049IYFWETFtTQ/TboWWKQemecNipWgxLAjqg)의 커뮤니티 기사를 참조할 수 있습니다.[[!DNL Workday] 

[!UICONTROL [!UICONTROL 문서 단계 검토]s]와(와) Adobe Sign을 사용하여 청구가능한 트랜잭션에는 1:1 관계가 있습니다. 하나의 [!UICONTROL 문서 단계 검토] 내에서 여러 문서를 결합할 수 있으며 서명을 위한 단일 패키지로 제공됩니다.

**참고**: 특정  ** 검토 문서 단계 내에서 단일 Dynamicdocument만 참조할 수  [!UICONTROL 있습니다].

[!UICONTROL 문서 검토 단계] 기능을 정의하려면

1. [!UICONTROL 문서 단계 검토]를 삽입합니다.
1. [!UICONTROL 문서 단계 검토]에서 수행할 수 있는 그룹(역할)을 지정하십시오.

![비즈니스 프로세스 단계](images/insert-review-doc-steptornm-575.png)

[!UICONTROL 문서 단계 검토]를 구성하려면 다음과 같이 하십시오.

1. *[!UICONTROL eSignature 통합 유형]*&#x200B;을 *[!UICONTROL eSign by Adobe]*&#x200B;으로 지정합니다.

1. 서명 격자에 행 추가.

   * 서명 격자는 서명을 받으러 문서가 라우팅되는 순차적인 순서를 지정합니다. 각 행에 한 개 이상의 역할을 지정할 수 있고 각 행이 서명 프로세스의 한 단계를 나타냅니다..
   * 특정 단계 내의 모든 역할의 구성원에게 서명 이벤트가 보류 중임을 알립니다.
   * 역할 기호에서 한 명의 사용자가 발생하면 행 단계가 완료되고 문서가 다음 행 단계로 이동됩니다.
   * 모든 행이 서명되면 [!UICONTROL 문서 단계 검토]가 완료됩니다.

1. 서명받을 문서를 지정합니다. 구인 BP인 경우 문서 생성 단계의 문서를 사용할 수 있습니다. 그렇지 않은 경우 기존 문서 또는 보고서를 선택하십시오.

1. 필요한 만큼 문서가 생길 때까지 3단계를 반복합니다..

   ![문서 검토 단계 구성](images/configure-rd-stepsmaller-575.png)

1. &#39;서명 거부&#39; 작업을 캡처하기 위해 &#39;리디렉션 사용자&#39;를 추가합니다(선택적). 사용자가 거부하면 [!DNL Workday]은(는) 검토를 위해 문서를 구성된 보안 그룹으로 재라우팅합니다.

[!UICONTROL 문서 단계 검토]의 관련 작업 메뉴에서 **[!UICONTROL 비즈니스 프로세스]** > **[!UICONTROL 리디렉션 유지 관리를 선택합니다.]** 다음 중 하나를 선택합니다.

* **[!UICONTROL 다시 보내기]**: 보안 그룹 구성원이 업무 프로세스의 이전 단계로 단계를 다시 보낼 수 있도록 하려면 비즈니스 프로세스가 해당 단계에서 다시 시작됩니다.
* **[!UICONTROL 다음 단계로 이동]**: 보안 그룹 구성원이 업무 프로세스의 다음 단계로 단계를 전달하도록 하려면
* **[!UICONTROL 보안 그룹]**: 비즈니스 프로세스 흐름의 단계를 리디렉션합니다. 이 프롬프트에 표시되는 보안 그룹은 리디렉션 섹션의 비즈니스 프로세스 보안 정책에서 선택됩니다.

## 업무 프로세스 단계 노트 {#business-process-step-notes}

비즈니스 프로세스 프레임워크는 강력합니다. 그러나 다음을 확인해야 합니다.

* 모든 업무 프로세스에는 완료 단계가 있어야 하며, 이는 업무 프로세스가 끝날 때 이상적으로 필요합니다.

* 검색 아이콘의 관련 작업 메뉴에서 완료 단계가 설정됩니다. 이 작업은 BP를 &quot;보고&quot;하는 동안에만 가능하며 &quot;편집&quot;하는 동안에는 불가능합니다.

* 비즈니스 프로세스의 모든 단계가 순차적으로 실행됩니다.

   주문 값을 변경하여 단계의 순서를 변경할 수 있습니다. 예를 들어, 항목 &quot;c&quot;와 &quot;d&quot; 사이에 단계를 삽입하려면 새 항목을 &quot;ca&quot;로 지정합니다.

### 예: 제안 {#example-offer}

제안 BP는 제안 BP를 실행하기 위해 구성해야 하는 Job Application Dynamic BP의 하위 프로세스입니다. 이 프로세스는 직무 지원 상태가 “구인” 또는 “구인하기(Make Offer)”로 바뀌는 경우에 트리거됩니다.

아래 예에서는 [!UICONTROL 문서 검토 단계]에서 북미 및 일본 모두에 대해 동적 문서 단계를 사용하고 있습니다.

![[!DNL Workday] 비즈니스 프로세스의 예](images/bp-for-offersmaller-575.png)

이 BP는 다음 작업을 수행합니다.

* BP의 개시자에게 후보자에 대한 보상을 제안하도록 요청합니다(b 단계).
* 단계 조건을 사용하여 현재 국가가 일본이 아닌지 테스트합니다.

   true이면 영어 문서를 사용하는 &quot;ba&quot; 단계를 실행합니다.

   false이면 일본어 문서를 사용하는 &quot;bb&quot; 단계를 실행합니다.

* [!UICONTROL 문서 단계 검토] &quot;bc&quot;에서 서명 프로세스를 정의합니다.
* 필요한 완료 단계 &quot;d&quot;에서 제안을 할 결정 지점을 정의합니다.

“ba”단계에서 생성되는 동적 문서를 [!UICONTROL 구인 공고(Offer Letter)]라고 하며 [!UICONTROL 긴급 구인(Rapid Offer)]이라고 적힌 텍스트 블록이 1개 포함되어 있습니다. 헤더, 인사말, 보상, 주식, 마감, 조건 등과 같은 여러 텍스트 블록을 필요에 따라 추가할 수 있습니다.

![[!DNL Workday] 문서 페이지 보기](images/offer-letter-575.png)

아래 동적 제안 문자는 [!DNL Workday] 서식 있는 텍스트 편집기에서 만들어집니다. *회색*&#x200B;에서 강조 표시된 항목은 컨텍스트 데이터를 참조하는 [!DNL Workday]에서 제공하는 개체입니다.

{{brackets}} 안의 항목은 [Adobe 텍스트 태그](https://adobe.com/go/adobesign_text_tag_guide_kr)입니다.

![동적 양식 예](images/script.png)

[!UICONTROL 문서 단계 검토] 내에서 동적 문서는 이전 단계에서 참조되며 두 서명 그룹을 통해 순차적 서명 프로세스를 정의합니다.

아래 그림에서는 동적으로 생성된 문서를 먼저 고용 관리자에게 전달한 다음 후보자에게 전달합니다.

![[!DNL Workday] 정의된 서명 그룹](images/configure-rd-stepsmaller-575.png)

### 예: 문서 배포 {#example-distribute-documents}

[!DNL Workday] 30에 소개된 문서 일괄 배포 또는 작업 작업을 사용하여 개별 서명자의 큰 그룹(&lt;20K)에 하나의 문서를 보낼 수 있습니다. 이 기능은 문서당 단일 서명으로 제한됩니다. 배포 만들기는 검색 표시줄에서 &#39;[!UICONTROL 문서 배포 만들기 또는 작업]&#39; 작업에 액세스하여 수행됩니다.

예: Global Modern Services의 모든 관리자에게 직원 형평성 선택 양식을 보냅니다. 원하는 경우 개별 관리자에게 추가로 필터링할 수 있습니다.

**문서 배포 보기 또는 작업** 보고서에 액세스하여 배포 진행률을 추적할 수도 있습니다.

![](images/create-distributedocumentsortasks.png)

### 예: 보고 {#example-reporting}

[!DNL Workday] 풍부한 보고 인프라를 갖추고 있습니다. Adobe Sign 프로세스의 세부 사항을 보려면 *문서 검토 이벤트*&#x200B;의 요소를 점검하십시오.

다음은 모든 BP에 걸쳐 Adobe Sign 트랜잭션과 그 상태를 알아보기 위해 실행할 수 있는 간단한 사용자 지정 보고서입니다.

![[!DNL Workday] 사용자 지정 보고서의 예](images/review-document-eventsmaller-575.png)

아래 보고서는 구현 임차인 내 구인, 입사 및 보상 제안 BP를 보고 생성되었습니다.

확인 가능한 항목:

* 서명을 받으러 발송된 문서
* 연결된 BP 단계
* 서명 대기 중인 다음 사람

![[!DNL Workday]세 개의 개체를 사용하는 보고서의 예](images/workday-reportsmaller-575.png)

## 서명된 문서 {#signed-documents}

[!DNL Workday] 서명 주기는 Adobe Sign에서 모든 전자 메일 알림을 표시하지 않습니다. 사용자는 [!DNL Workday] 받은 편지함 내에서 보류 중인 작업에 대해 알게 됩니다.

모든 서명 그룹에서 문서에 서명하면 서명된 문서의 복사본이 전자 메일을 통해 서명 그룹의 모든 구성원에게 배포됩니다.

이 동작을 방지하려면 Adobe Sign Success Manager 또는 [Adobe Sign Support 팀](https://adobe.com/go/adobesign-support-center)에 문의하십시오.

[!DNL Workday] 내에서 전체 프로세스 레코드에서 서명된 문서에 액세스할 수 있습니다. 다음을 찾을 수 있습니다.

* 작업자 프로파일의 작업자 문서 및
* 후보 프로필의 후보 문서(제안 서신)

아래 그림은 Chris Foxx 후보자를 위한 서명된 제안 서신을 보여줍니다.

![제안  [!DNL Workday] 편지 예](images/offer.png)

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

Adobe Sign 고객은 담당 고객 성공 관리자(CSM)에게 지원을 요청해야 합니다. 또는 Adobe 기술 지원(전화: 1-866-318-4100)에 전화하여 제품 목록이 나오면 4번에 이어 2번(전화 안내에 따라)을 누르면 됩니다.

* [문서에 Adobe 텍스트 태그 추가하기](https://adobe.com/go/adobesign_text_tag_guide)

<!--
[Download PDF](images/adobe-sign-for-workday-quick-start-guide-2016.pdf)
-->
