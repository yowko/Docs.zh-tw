---
ms.openlocfilehash: b861dbaa02c97a03c015fdf4e63d25c40c90ea0a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721255"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a>遵守 SignedCms 的布林值參數。 ComputeSignature

在 .NET Core 中， `silent` 會遵守方法的布林值參數 <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> 。 如果此參數設定為，則不會顯示 PIN 提示 `true` 。

#### <a name="change-description"></a>變更描述

在 .NET Framework 中， `silent` <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> 會忽略方法的參數，而且在提供者需要時，一律會顯示 PIN 提示。 在 .NET Core 中， `silent` 會遵守參數，如果設定為，則永遠不會 `true` 顯示 PIN 提示（即使提供者需要）。

2.1 版的 .NET Core 中引進了 CMS/PKCS #7 訊息的支援。

#### <a name="version-introduced"></a>引進的版本

2.1

#### <a name="recommended-action"></a>建議的動作

為確保在需要時顯示 PIN 提示，桌面應用程式應該呼叫， <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> 並將布林參數設定為 `false` 。 產生的行為等同于 .NET Framework，不論是否在該處停用無訊息內容。

#### <a name="category"></a>類別

密碼編譯

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
