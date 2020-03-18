---
ms.openlocfilehash: 7f528510e4158dad71280a7b1f269a231b8c60f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116370"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Microsoft 中的類型.VisualBasic.設備命名空間不可用

命名空間中<xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>的類型不可用。

#### <a name="version-introduced"></a>介紹的版本

.NET 核心 3.0 預覽 8

#### <a name="change-description"></a>變更描述

命名空間中<xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>的類型在某些 .NET Core 3.0 預覽版本中可用。 它們不再可用，從 .NET 核心 3.0 預覽 9 開始。

已刪除這些類型，以避免不必要的程式集依賴關係或後續版本中的中斷更改。

#### <a name="recommended-action"></a>建議的動作

如果代碼取決於類型及其成員的使用<xref:Microsoft.VisualBasic.Devices>，則可以在 .NET 類庫中使用相應的類型或成員。 例如<xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType>，類的等效功能由<xref:System.DateTime?displayProperty=nameWithType>和<xref:System.Environment?displayProperty=nameWithType>類型提供，並且<xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType>與類的等效功能由命名空間中的<xref:System.IO.Ports?displayProperty=nameWithType>類型提供。

#### <a name="category"></a>類別

Visual Basic

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
