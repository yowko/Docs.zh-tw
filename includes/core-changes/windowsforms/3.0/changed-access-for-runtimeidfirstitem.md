---
ms.openlocfilehash: 1ea2d70a7cfe04cc4c4b9b58ea6bb6fa0226b245
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721145"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>變更 AccessibleObject 的存取權。 RuntimeIDFirstItem

從 .NET Core 3.0 RC1 開始，的存取範圍 `AccessibleObject.RuntimeIDFirstItem` 已從變更 `protected` 為 `internal` 。

#### <a name="change-description"></a>變更描述

從 .NET Core 3.0 Preview 4 開始， `AccessibleObject.RuntimeIDFirstItem` 欄位為 `protected` 。 從 .NET Core 3.0 RC1 開始，它已從變更為， `protected` `internal` 以配合 .NET Framework 中欄位的存取範圍。

#### <a name="version-introduced"></a>引進的版本

3.0 RC1

#### <a name="recommended-action"></a>建議的動作

如果您開發的 .NET Core 應用程式具有衍生自的類型 <xref:System.Windows.Forms.AccessibleObject> ，並存取欄位，則變更可能會影響您 `RuntimeIDFirstItem` 。 如果是這種情況，您可以定義本機常數，如下所示：

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- 無法透過 API 分析來偵測。

<!-- 

#### Affected APIs

- Not detectable via API analysis.

-->
