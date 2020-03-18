---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449208"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a>簽名Cms的布林參數.計算簽名得到尊重

在 .NET Core 中`silent`，<xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>該方法的布林參數得到尊重。 如果此參數設置為`true`，則不顯示 PIN 提示。

#### <a name="change-description"></a>變更描述

在 .NET 框架`silent`中，將<xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>忽略該方法的參數，並且如果提供程式需要，則始終顯示 PIN 提示。 在 .NET Core`silent`中，該參數受到尊重，如果`true`設置為 ，則永遠不會顯示 PIN 提示符，即使提供程式需要 PIN 提示符也是如此。

對 CMS/PKCS 的支援#7消息在 2.1 版中引入到 .NET Core 中。

#### <a name="version-introduced"></a>介紹的版本

2.1

#### <a name="recommended-action"></a>建議的動作

為確保在需要時出現 PIN 提示，桌面應用程式應調用<xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>並將布林參數設置為`false`。 無論靜默上下文是否在那裡被禁用，生成的行為與 .NET 框架上的行為相同。

### <a name="category"></a>類別

Cryptography

### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
