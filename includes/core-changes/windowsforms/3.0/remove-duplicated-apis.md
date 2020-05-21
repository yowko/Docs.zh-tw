---
ms.openlocfilehash: 3dfacadb5127319d4ce27f367803637cfb1ed00f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721080"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>已從 Windows Forms 移除重複的 Api

從 .NET core 3.0 Preview 4 開始，命名空間中不小心重複的一些 Api 已 <xref:System.Windows.Forms?displayProperty=fullName> 從 .Net core 3.0 RC1 中移除。

#### <a name="change-description"></a>變更描述

.NET Core 3.0 Preview 4 不小心複製了命名空間中已經存在的一些類型 <xref:System.Windows.Forms?displayProperty=fullName> <xref:System.ComponentModel.Design?displayProperty=fullName> 。 從 .NET Core 3.0 RC1 開始，這些重複的類型已無法再使用。 下表顯示原始類型和其重複類型的清單：

> [!div class="mx-tdCol2BreakAll"]
> |原始類型|重複的類型|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a>引進的版本

3.0 RC1

#### <a name="recommended-action"></a>建議的動作

更新程式碼以參考原始類型，如資料表的**原始類型**資料行所示。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- 無。

<!--

#### Affected APIs

- Not detectable via API analysis.

-->
