---
title: FIPS 合規性-.NET Core
description: 說明 .NET Core 聯邦資訊處理標準（FIPS）合規性。
ms.date: 11/20/2019
author: Rick-Anderson
ms.author: riande
ms.openlocfilehash: 84d6edc6975af0484bb67999ad5891eaf4db057d
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626954"
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
* [第8章。美國聯邦標準和法規 Red Hat Enterprise Linux 7](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/security_guide/chap-federal_standards_and_regulations)
