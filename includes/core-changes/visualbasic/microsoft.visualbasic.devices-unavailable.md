---
ms.openlocfilehash: bb163d5a6eb3d926a44a83ea79572c3a497bbe8d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181766"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Microsoft 中的類型命名空間無法使用

<xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>命名空間中的類型無法使用。

#### <a name="version-introduced"></a>引進的版本

.NET Core 3.0 Preview 8

#### <a name="details"></a>詳細資料

<xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>命名空間中的類型可在某些 .net Core 3.0 Preview 版本中取得。 從 .NET Core 3.0 Preview 9 開始就不再提供這些功能。

已移除類型，以避免不必要的元件相依性或後續版本中的重大變更。
 
#### <a name="recommended-action"></a>建議的動作

如果您的程式碼相依于<xref:Microsoft.VisualBasic.Devices>類型及其成員的使用，您可以在 .net 類別庫中使用對應的類型或成員。 例如<xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> ，類別的對等功能是<xref:System.DateTime?displayProperty=nameWithType>由和<xref:System.Environment?displayProperty=nameWithType>類型提供，而<xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType>類別的對等功能則是由<xref:System.IO.Ports?displayProperty=nameWithType>命名空間中的類型提供。

#### <a name="category"></a>分類

Visual Basic

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

