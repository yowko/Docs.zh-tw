---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644044"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>變更 AccessibleObject 的存取權。 RuntimeIDFirstItem

從 .NET Core 3.0 RC1 開始，`AccessibleObject.RuntimeIDFirstItem` 的存取範圍從 `protected` 變更為 `internal`。

#### <a name="change-description"></a>變更描述

從 .NET Core 3.0 Preview 4 開始，`AccessibleObject.RuntimeIDFirstItem` 欄位已 `protected`。 從 .NET Core 3.0 RC1 開始，它已從 `protected` 變更為 `internal`，以配合 .NET Framework 中欄位的存取範圍。

#### <a name="version-introduced"></a>引進的版本

3.0 RC1

#### <a name="recommended-action"></a>建議的動作

如果您開發的 .NET Core 應用程式具有衍生自 <xref:System.Windows.Forms.AccessibleObject> 的類型，並存取 `RuntimeIDFirstItem` 欄位，則變更可能會影響您。 如果是這種情況，您可以定義本機常數，如下所示：

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a>Category

Windows 表單

#### <a name="affected-apis"></a>受影響的 API

- 無法透過 API 分析來偵測。

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
