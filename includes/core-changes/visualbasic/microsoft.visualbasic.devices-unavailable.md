---
ms.openlocfilehash: dae4afa92b8833f326b4eacd00b36bb3e1199cc1
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237308"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Microsoft 中的類型命名空間無法使用

@No__t 0 命名空間中的類型無法使用。

#### <a name="version-introduced"></a>引進的版本

.NET Core 3.0 Preview 8

#### <a name="change-description"></a>變更描述

在某些 .NET Core 3.0 Preview 版本中，可以使用 <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> 命名空間中的類型。 從 .NET Core 3.0 Preview 9 開始就不再提供這些功能。

已移除類型，以避免不必要的元件相依性或後續版本中的重大變更。
 
#### <a name="recommended-action"></a>建議的動作

如果您的程式碼相依于使用 @no__t 0 型別及其成員，您可以在 .NET 類別庫中使用對應的型別或成員。 例如，對 @no__t 0 類別的對等功能是由 <xref:System.DateTime?displayProperty=nameWithType> 和 @no__t 2 類型所提供，而 <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> 類別的對等功能則是由 <xref:System.IO.Ports?displayProperty=nameWithType> 命名空間中的類型所提供。

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

