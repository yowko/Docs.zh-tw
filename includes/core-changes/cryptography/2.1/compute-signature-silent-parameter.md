---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449208"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a>遵守 SignedCms 的布林值參數。 ComputeSignature

在 .NET Core 中，會遵守 <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> 方法的布林值 `silent` 參數。 如果此參數設定為 [`true`]，則不會顯示 PIN 提示。

#### <a name="change-description"></a>變更描述

在 .NET Framework 中，會忽略 <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> 方法的 `silent` 參數，並在提供者要求時一律顯示 PIN 提示。 在 .NET Core 中，會遵守 `silent` 參數，如果設定為 `true`，則永遠不會顯示 PIN 提示（即使提供者需要）。

2\.1 版的 .NET Core 中引進了 CMS/PKCS #7 訊息的支援。

#### <a name="version-introduced"></a>引進的版本

2.1

#### <a name="recommended-action"></a>建議的動作

為確保在需要時顯示 PIN 提示，桌面應用程式應該呼叫 <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> 並將布林參數設定為 `false`。 產生的行為等同于 .NET Framework，不論是否在該處停用無訊息內容。

### <a name="category"></a>類別

Cryptography

### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
