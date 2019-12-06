---
title: FIPS 合規性-.NET Core
description: 說明 .NET Core 聯邦資訊處理標準（FIPS）合規性。
ms.date: 11/20/2019
author: Rick-Anderson
ms.author: riande
ms.openlocfilehash: cf640c857e79ae811dd38d57a0e5301b7bc96572
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74205063"
---
# <a name="net-core-federal-information-processing-standard-fips-compliance"></a>.NET Core 聯邦資訊處理標準（FIPS）合規性

聯邦資訊處理標準（FIPS）發行集140-2 是美國政府標準，定義資訊技術產品中密碼編譯模組的最低安全性需求，如資訊第5131節所定義.1996的技術管理改革動作。

.NET Core：

* 會將密碼編譯基本呼叫傳遞至基礎作業系統所提供的標準模組。
* 不**會強制在**.net Core 應用程式中使用 FIPS 已核准的演算法或金鑰大小。

系統管理員負責設定作業系統的 FIPS 合規性。

如果程式碼是針對符合 FIPS 規範的環境所撰寫，則開發人員會負責確保不會使用不相容的 FIPS 演算法。

如需 FIPS 合規性的詳細資訊，請參閱下列文章：

* [Windows FIPS 合規性](/windows/security/threat-protection/fips-140-validation)
* [設定 Windows 以符合 FIPS 規範](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
* [10.2. 聯邦資訊處理標準（FIPS）](https://access.redhat.com/documentation/red_hat_enterprise_linux/6/html/security_guide/sect-security_guide-federal_standards_and_regulations-federal_information_processing_standard)
