---
ms.openlocfilehash: 4c47b95e98aca727d9f0eda54a167a71fd53afb9
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567419"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Microsoft 中的類型命名空間無法使用

<xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> 命名空間中的類型無法使用。

#### <a name="version-introduced"></a>引進的版本

.NET Core 3.0 Preview 8

#### <a name="change-description"></a>變更描述

在某些 .NET Core 3.0 Preview 版本中，可以使用 <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> 命名空間中的類型。 從 .NET Core 3.0 Preview 9 開始就不再提供這些功能。

已移除類型，以避免不必要的元件相依性或後續版本中的重大變更。

#### <a name="recommended-action"></a>建議的動作

如果您的程式碼相依于 <xref:Microsoft.VisualBasic.Devices> 類型及其成員的使用，您可以在 .NET 類別庫中使用對應的類型或成員。 例如，<xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> 類別的對等功能是由 <xref:System.DateTime?displayProperty=nameWithType> 和 <xref:System.Environment?displayProperty=nameWithType> 類型提供，而 <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> 類別的對等功能則是由 <xref:System.IO.Ports?displayProperty=nameWithType> 命名空間中的類型所提供。

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

