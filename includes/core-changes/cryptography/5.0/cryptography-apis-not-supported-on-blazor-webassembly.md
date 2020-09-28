---
ms.openlocfilehash: 6c2aff4abf558307d599ff7533c82286e037bc71
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406140"
---
### <a name="systemsecuritycryptography-apis-not-supported-on-blazor-webassembly"></a>Blazor WebAssembly 不支援的密碼編譯 Api

<xref:System.Security.Cryptography> Api 會在 <xref:System.PlatformNotSupportedException> 執行時間于瀏覽器上執行時擲回。

#### <a name="change-description"></a>變更描述

在舊版的 .NET 中，大部分的 <xref:System.Security.Cryptography> api 無法用來 Blazor WebAssembly 應用程式。 從 .NET 5.0 開始，Blazor WebAssembly apps 會以完整的 .NET 5 API 介面區為目標，不過，由於瀏覽器沙箱條件約束，不支援所有的 .NET 5 Api。 在 .NET 5.0 和更新版本中，不支援的 api 會在 <xref:System.Security.Cryptography> <xref:System.PlatformNotSupportedException> WebAssembly 上執行時擲回。

> [!TIP]
> 當您建立支援瀏覽器平臺的專案時， [平臺相容性分析器](../../../../docs/core/compatibility/code-analysis.md#ca1416-platform-compatibility) 會將任何對受影響 api 的呼叫加上旗標。 此分析器預設會在 .NET 5.0 和更新版本的應用程式中執行。

#### <a name="reason-for-change"></a>變更的原因

Microsoft 無法以 Blazor WebAssembly 設定中的相依性來傳送 OpenSSL。 我們嘗試與瀏覽器的 API 整合來解決此問題 `SubtleCrypto` 。 可惜的是，它需要大量的 API 變更，使其難以整合。

#### <a name="version-introduced"></a>引進的版本

5.0 RC1

#### <a name="recommended-action"></a>建議的動作

目前沒有建議的好方法可提供建議。

#### <a name="category"></a>類別

- ASP.NET Core
- 密碼編譯

#### <a name="affected-apis"></a>受影響的 API

<xref:System.Security.Cryptography?displayProperty=fullName>除了下列以外的所有 api：

- `System.Security.Cryptography.RandomNumberGenerator`
- `System.Security.Cryptography.IncrementalHash`
- `System.Security.Cryptography.SHA1`
- `System.Security.Cryptography.SHA256`
- `System.Security.Cryptography.SHA384`
- `System.Security.Cryptography.SHA512`
- `System.Security.Cryptography.SHA1Managed`
- `System.Security.Cryptography.SHA256Managed`
- `System.Security.Cryptography.SHA384Managed`
- `System.Security.Cryptography.SHA512Managed`

<!--

#### Affected APIs

- `T:System.Security.Cryptography`

-->
