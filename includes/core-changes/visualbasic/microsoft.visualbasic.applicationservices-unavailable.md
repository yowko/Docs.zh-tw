---
ms.openlocfilehash: d888aba597cb6981828ca67fba04912cbcf7935f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198369"
---
### <a name="types-in-microsoftvisualbasicapplicationservices-namespace-not-available"></a>Microsoft.visualbasic.applicationservices.cantstartsingleinstanceexception 命名空間中的類型無法使用

<xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> 命名空間中的類型無法使用。

#### <a name="version-introduced"></a>引進的版本

.NET Core 3.0 Preview 8

#### <a name="change-description"></a>變更描述

在某些 .NET Core 3.0 Preview 版本中，可以使用 <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> 命名空間中的類型。 從 .NET Core 3.0 Preview 9 開始就不再提供這些功能。

已移除類型，以避免不必要的元件相依性或後續版本中的重大變更。

#### <a name="recommended-action"></a>建議的動作

如果您的程式碼相依于 <xref:Microsoft.VisualBasic.ApplicationServices> 類型及其成員的使用，您可以在 .NET 類別庫中使用對應的類型或成員。 例如，某些 <xref:System.Environment?displayProperty=nameWithType> 和 <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> 成員會將對等的功能提供給 <xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType> 類別的屬性。

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.ApplicationServices`

-- >

