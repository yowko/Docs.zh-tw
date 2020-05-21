---
ms.openlocfilehash: a35de09b9a7bb9686433205359c3cc55954c29c3
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721476"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Microsoft 中的類型命名空間無法使用

命名空間中的類型 <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> 無法使用。

#### <a name="version-introduced"></a>引進的版本

.NET Core 3.0 Preview 8

#### <a name="change-description"></a>變更描述

命名空間中的類型 <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> 可在某些 .Net Core 3.0 Preview 版本中取得。 從 .NET Core 3.0 Preview 9 開始就不再提供這些功能。

已移除類型，以避免不必要的元件相依性或後續版本中的重大變更。

#### <a name="recommended-action"></a>建議的動作

如果您的程式碼相依于 <xref:Microsoft.VisualBasic.Devices> 類型及其成員的使用，您可以在 .net 類別庫中使用對應的類型或成員。 例如，類別的對等功能 <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> 是由 <xref:System.DateTime?displayProperty=nameWithType> 和 <xref:System.Environment?displayProperty=nameWithType> 類型提供，而類別的對等功能 <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> 則是由命名空間中的類型提供 <xref:System.IO.Ports?displayProperty=nameWithType> 。

#### <a name="category"></a>類別

Visual Basic

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
