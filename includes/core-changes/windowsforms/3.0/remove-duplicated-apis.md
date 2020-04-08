---
ms.openlocfilehash: 0be59258df10aa13920551f011d68bc8efe20b93
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888104"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a>從 Windows 表單中移除的重複 API

在 .NET Core<xref:System.Windows.Forms?displayProperty=fullName>3.0 預覽 4 中啟動的命名空間中意外複製了許多 API,已在 .NET Core 3.0 RC1 中刪除。

#### <a name="change-description"></a>變更描述

.NET Core 3.0 預覽 4<xref:System.Windows.Forms?displayProperty=fullName><xref:System.ComponentModel.Design?displayProperty=fullName>無意中複製了 命名空間中已經存在的命名空間中的許多類型。 從 .NET Core 3.0 RC1 開始,這些重複的類型不再可用。 下表列的原始型態與重複型態:

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

更新代碼以引用原始類型,如表**的"原始類型**"列所示。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- 無。

<!--

### Affected APIs

- Not detectable via API analysis.

-->
