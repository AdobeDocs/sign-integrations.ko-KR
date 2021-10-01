---
title: NetSuite용 Adobe Sign 릴리스 정보
description: 'NetSuite용 Adobe Sign 통합의 현재 릴리스에 포함된 새로운 기능과 변경 사항에 대해 알아봅니다.  '
type: Documentation
solution: Adobe Sign
role: User, Developer
topic: Integrations
source-git-commit: 924813403d8e13f816347dd548a68a16d78d866e
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 67%

---


# NetSuite용 Adobe Sign 릴리스 정보

## 패키지 v4.0.4로 업데이트

4.0.4에서는 새로 생성된 모든 트래픽에 계정별 도메인을 사용하도록 조정되었습니다.

Adobe Sign 아이콘이 새 이미지로 업데이트되었습니다.

## 이전 릴리스

### NetSuite용 Adobe Sign 4.0.4

4.0.4에서는 새로 생성된 모든 트래픽에 계정별 도메인을 사용하도록 조정되었습니다.

Adobe Sign 아이콘이 새 이미지로 업데이트되었습니다.

### NetSuite용 Adobe Sign 4.0.2

**Adobe Sign**(*Adobe Document Cloud eSign 서비스*&#x200B;에서)으로 다시 브랜드\
이전에 *Adobe eSign Services*&#x200B;를 재브랜딩의 증거로 본 *Adobe Sign*&#x200B;이 표시됩니다.

### NetSuite용 Adobe Sign 4.0.1

NetSuite에서 플랫폼 업데이트를 할 때 발생하는 API 회귀 버그로 인해, 새로운 패키지(v4.0.1)가 릴리스되었습니다.

최신 패키지로 업데이트하는 것이 권장됩니다.

### NetSuite용 Adobe Sign 4.0

**NetSuite를 통한 사용자 자동 프로비저닝이 추가되었음**

v4.0에 대한 새로운 사용자 정의 환경 설정이 추가되었습니다. 이 설정이 활성화되면 NetSuite에서 계약서를 보내는 사용자는 Adobe Document Cloud eSign 서비스 사용자 계정으로 자동 프로비저닝됩니다.

**&#39;Built for NetSuite&#39; 인증**

이 버전은 &#39;NetSuite용으로 개발&#39; 인증을 획득했으며, 모든 최신 NetSuite 모범 사례에 맞게 설계되었습니다.

**Adobe Document Cloud eSign 서비스로 브랜드 변경(EchoSign에서)**

브랜드 변경의 증거로, 이전에 Adobe EchoSign을 보셨던 곳에서 Adobe Document Cloud eSign 서비스(또는 줄여서 Adobe eSign 서비스)를 보시게 될 것입니다.

**OAuth를 사용하여 보안 강화**

데이터 보안을 개선하기 위해 eSign 서비스는 이제 OAuth 2.0을 사용하여 NetSuite에서 Adobe Document Cloud eSign 서비스 계정을 인증합니다. 새 프로토콜을 사용하면 NetSuite가 eSign 서비스 암호를 요청하지 않고도, eSign 서비스와 연결할 수 있습니다. 중요한 정보가 앱 간에 직접 공유되지 않으므로 계정이 손상될 가능성이 작습니다. 이 개선 사항은 사용자의 구현에는 영향을 주지 않지만 Adobe Document Cloud와 통신하려면 일회성 설정을 수행하여 NetSuite 패키지를 인증해야 합니다. 이것은 설치 프로세스 중에 수행됩니다. 패키지의 이전 버전(v3.5.9 이하)에서 업그레이드하는 고객의 경우 이전에 사용한 API 키가 인증 프로세스 중에 생성된 OAuth 토큰으로 대체됩니다.

**SOAP API에서 REST API로 eSign 서비스를 마이그레이션했습니다.**

효율성, 유연성 및 처리 속도를 향상시키기 위해 Adobe Document Cloud eSign 서비스와 NetSuite에 대한 v4.0 통합은 SOAP 기반에서 REST 기반 API로 마이그레이션되었습니다.

### NetSuite용 Adobe Sign 3.0

**고급 참여자 역할 - 승인자**

* 계약에서 한 명 이상의 수신자를 승인자로 표시할 수 있습니다.
* 승인자는 문서를 검토하고 승인해야 합니다.
* 승인자는 또한 승인하기 전, 계약서에 데이터를 입력해야 할 수도 있습니다.

**문서 미리 보기 또는 전송 전 양식 필드 끌어서 놓기**

서명을 위해 보내기 전에 계약 미리 보기 또는 양식 필드를 끌어 놓기

**현재 서명자에게 알림 메시지 전송**

현재 서명자에게 즉시 알림 메시지 전송

**고급 서명자 인증 정책**

* **지식 기반 인증:** 서명자 ID를 확인하기 위한 질문에 응답
   * 서명자는 공용 및 상업용 데이터베이스에서 가져온 수백 개의 질문에 대답하여 자신의 ID를 증명해야 합니다.
   * 서명의 이름은 사용자의 인증된 이름에서 가져오며 서명 시 변경할 수 없습니다.
   * RSA 제공
   * KBA 사용은 계정별, 월별로 제한됩니다. 자세한 내용은 영업 담당자에게 문의하십시오.

* **웹 ID:** 로그인하기 전에 Facebook, LinkedIn, Google 또는 기타 타사 웹 서비스로 로그인하세요.

   * 서명자는 타사 웹 서비스를 사용하여 자신의 ID를 확인한 후에만 서명할 수 있습니다.
   * 서명의 이름은 사용자의 웹 서비스 프로필에서 가져오며 서명 시 변경할 수 없습니다.
   * 감사 추적은 ID 확인 세부 정보를 캡처합니다.

* **일회용 암호**
   * 내/외부 서명자 또는 모든 서명자에 대해 인증 방법을 적용합니다. 내부 서명자가 암호를 사용하지 않는 동안 외부 서명자는 암호를 사용하거나 기술 기반 인증을 사용해야 합니다.

**추가 사용자 지정 기본 설정**

* 서명된 PDF를 !le URL에 대한 링크로 추가하거나 NetSuite에서 호스팅되는 첨부 파일로 추가
* 계약서에 서명한 후 계약 기록에 감사 추적을 추가합니다.
* 기본적으로 고객 전자 메일 대신 트랜잭션 연락처를 첫 번째 서명자로 사용합니다.
* 전송자에게 수신자를 승인자로 표시하는 옵션을 부여합니다.

**트랜잭션 파일**

새 &#39;트랜잭션 파일&#39; 드롭다운 목록을 사용하여 현재 트랜잭션에서 첨부할 파일을 선택할 수 있습니다.

**모든 EchoSign 문서에 대한 Adobe PDF 인증서**

* EchoSign에서 보내거나 다운로드한 모든 PDF 파일은 Adobe EchoSign 디지털 인증서로 인증됩니다.
* Acrobat 또는 Reader는 추가 신뢰와 안심을 위해 문서가 변경되지 않았음을 보증하는 인증서를 표시합니다.

**지원 문서 수집**

* 전송자는 서명하는 동안 서명자로부터 추가 지원 문서(예 : 운전 면허증, 비즈니스 인증서)를 수집할 수 있습니다.
* 수집된 문서는 서명된 계약의 공식 기록 중 일부가 됩니다.

**조건부 데이터 필드**

* 계약 필드에서의 조건부 논리를 정의합니다.
* 조건은 계약에서 하나 이상의 필드 값을 기반으로 할 수 있습니다.
* 조건은 양식 작성 UI 끌어서 놓기 또는 텍스트 태그를 통해 정의할 수 있습니다.
* 서명자는 de!ned 조건에 따라 문서에 서명할 때 적절한 필드를 제공합니다.

**추가적인 EchoSign 양식 필드 개선 사항**

* 드롭다운 메뉴
* 필드 마스크 지정
* 라디오 단추
* 문서 구조를 유지하기 위해 짧은 텍스트 태그를 만듭니다.