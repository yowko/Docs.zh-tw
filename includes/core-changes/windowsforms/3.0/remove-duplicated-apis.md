---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937084"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>從 Windows 表單中刪除的重複 API

在 .NET Core 3.0<xref:System.Windows.Forms?displayProperty=fullName>預覽 4 中啟動的命名空間中意外複製了許多 API，已在 .NET Core 3.0 RC1 中刪除。

#### <a name="change-description"></a>變更描述

.NET Core 3.0 預覽 4 無意中複製了<xref:System.Windows.Forms?displayProperty=fullName><xref:System.ComponentModel.Design?displayProperty=fullName>命名空間中已經存在的命名空間中的許多類型。 從 .NET Core 3.0 RC1 開始，這些重複的類型不再可用。 下表列出了原始類型及其重複類型：

> [!div class="mx-tdCol2BreakAll"]
> |原始類型|重複類型|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a>介紹的版本

3.0 RC1

#### <a name="recommended-action"></a>建議的動作

更新代碼以引用原始類型，如表**的"原始類型**"列所示。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- 無法通過 API 分析檢測。

<!--

### Affected APIs

- Not detectable via API analysis.

-->
