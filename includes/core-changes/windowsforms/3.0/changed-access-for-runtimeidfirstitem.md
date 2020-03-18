---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74644044"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a>更改可訪問物件的訪問. 運行時 ID 第一專案

從 .NET Core 3.0 RC1`AccessibleObject.RuntimeIDFirstItem`開始，的`protected`可`internal`訪問性從 更改為 。

#### <a name="change-description"></a>變更描述

從 .NET 核心 3.0 預覽`AccessibleObject.RuntimeIDFirstItem`4`protected`開始，該欄位為 。 從 .NET Core 3.0 RC1 開始`protected`，`internal`它已更改為 與 .NET 框架中欄位的可訪問性一致。

#### <a name="version-introduced"></a>介紹的版本

3.0 RC1

#### <a name="recommended-action"></a>建議的動作

如果您開發了 .NET Core 應用，其類型派生自<xref:System.Windows.Forms.AccessibleObject>並訪問`RuntimeIDFirstItem`該欄位，則更改可能會影響您。 如果是這種情況，您可以定義本地常量，如下所示：

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- 無法通過 API 分析檢測。

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
