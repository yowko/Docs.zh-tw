---
ms.openlocfilehash: d8cc506d60f3c24087ebde8ead345656fea0f484
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116381"
---
### <a name="types-in-microsoftvisualbasicapplicationservices-namespace-not-available"></a>Microsoft 中的類型.VisualBasic.應用程式服務命名空間不可用

命名空間中<xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>的類型不可用。

#### <a name="version-introduced"></a>介紹的版本

.NET 核心 3.0 預覽 8

#### <a name="change-description"></a>變更描述

命名空間中<xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>的類型在某些 .NET Core 3.0 預覽版本中可用。 它們不再可用，從 .NET 核心 3.0 預覽 9 開始。

已刪除這些類型，以避免不必要的程式集依賴關係或後續版本中的中斷更改。

#### <a name="recommended-action"></a>建議的動作

如果代碼取決於類型及其成員的使用<xref:Microsoft.VisualBasic.ApplicationServices>，則可以在 .NET 類庫中使用相應的類型或成員。 例如，某些<xref:System.Environment?displayProperty=nameWithType>和<xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType>成員提供與<xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType>類的屬性等效的功能。

#### <a name="category"></a>類別

Visual Basic

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.ApplicationServices`

-->
