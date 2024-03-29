---
title: Adobe Sign 통합 제품 버전 및 수명 주기
description: Adobe Sign 통합 버전 및 지원 수명 주기에 대해 알아보기
audience: External
products: Adobe Sign
type: Documentation
solution: Acrobat Sign
role: User, Developer
topic: Integrations
exl-id: c1f22848-7951-4066-84d4-f8cf6c2f3a6f
source-git-commit: 4d73ff36408283805386bd3266b683bc187d6031
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# 제품 버전 및 수명 주기 {#version}

통합 서비스에 대한 Adobe Sign 버전 관리 규칙 및 지원 라이프사이클은 사용자가 익숙한 다른 Adobe 제품과 정렬됩니다.

## 버전 번호

패키지 버전은 세 부분으로 된 번호 지정 시스템을 사용하여 릴리스된 버전의 순차 빌드 번호를 식별하고 새 컨텐츠 또는 변경 중인 컨텐츠 측면에서 업그레이드의 상대적 가져오기를 식별합니다.

버전 번호는 다음 패턴을 따릅니다. N.m.p

여기서, N = 주 버전; m = 부 버전; p = 패치 버전.

예를 들어 통합 패키지 버전 23.2.1은 다음과 같은 릴리스 상태를 나타냅니다.

* 주 버전: 23
* 부 버전: 2
* 패치 버전: 1

엔지니어가 패키지의 새 &quot;빌드&quot;를 개발할 때 코드에 대한 업데이트의 특성에 따라 버전 번호를 증가시킵니다.

* 주요 버전 변경은 기능에 대한 중요한 추가 또는 핵심 시스템에 대한 중요한 변경을 포함합니다.
* 부 버전 업데이트에는 더 작은 기능 업데이트 및 보안 패치가 포함됩니다. 보안 업데이트가 있거나 보고된 항목을 처리하기 위해 Adobe Sign을 최신 패치 버전으로 업그레이드해야 할 수 있습니다.
* 패치 버전은 거의 대부분 버그 수정 및 UI 조정입니다

>[!NOTE]
>
>제품이 개발 시 반복되므로 모든 버전이 공개되지 않습니다. 따라서 릴리스 간 패치 버전에 상당한 차이가 있을 수 있습니다.

관리자는 계정에 모든 기능에 대한 전체 액세스 권한을 가지고 알려진 모든 보안 문제에 패치를 적용할 수 있도록 최신 버전을 유지해야 합니다. 보안 문제가 있거나 중요한 시스템 문제를 해결하기 위해 Adobe Sign을 최신 패치 버전으로 업그레이드해야 할 수 있습니다.

## 버전 지원 수명 주기

Adobe Sign 통합 제품의 버전 지원 수명 주기는 패키지의 주 버전에 따라 정의되며 Adobe Sign에서 개별 통합 버전을 원활하게 지원하는 시간대를 표시합니다.

Adobe Sign은 패키지의 현재 버전과 이전 2개의 주요 버전(관련된 모든 부 버전 및 패치 업데이트 포함)을 지원합니다. 주요 버전은 다음과 같이 표시됩니다.

* 현재 버전(N): 패키지의 최신 주요 버전
* 이전 버전(N-1): 최신 버전의 주요 버전
* 마지막 지원 버전(N-2): 현재 버전 뒤의 두 주요 버전

예를 들어 현재 사용 가능한 패키지 버전이 23.2.1 인 경우:

* 현재 주 버전(N)은 23입니다.
* 이 패키지의 이전 주 버전(N-1)은 22입니다.
* 이 패키지의 마지막 지원 주 버전(N-2)은 21입니다.
* 21.0.0 이전 버전은 모두 지원되지 않습니다.

![버전 차트](images/version_chart.png)

## 버전 서비스 수명 주기

버전 서비스 수명 주기는 서비스를 사용할 수 있는 시간의 전체 범위를 정의합니다. 타임라인은 버전 지원 수명 주기에 업그레이드를 완료하는 데 사용할 수 있는 90일의 유예 기간을 추가한 것과 같습니다.

* 지원되지 않는 버전의 유예 기간 동안에는 지원되지 않는 버전을 유지하지 않고 최신 버전으로 업그레이드하기 위한 지원만 제공됩니다
* 유예 기간이 지나면 버전이 서비스되지 않습니다

* Adobe Sign은 서비스가 중단된 버전의 요청을 수락하지 않습니다.
* 통합이 현재 버전으로 업그레이드되면 Adobe Sign과 통합 간 통신이 정상적으로 재개됩니다

![종료 기간](images/shutdown_period.png)

질문이 있는 경우 리셀러 또는 고객 지원에 문의하십시오.
