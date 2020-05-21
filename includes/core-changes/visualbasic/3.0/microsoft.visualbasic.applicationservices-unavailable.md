---
ms.openlocfilehash: 09027863ff2f0009a14578db35db870c27369726
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721234"
---
### <a name="types-in-microsoftvisualbasicapplicationservices-namespace-not-available"></a>Microsoft.visualbasic.applicationservices.cantstartsingleinstanceexception 命名空間中的類型無法使用

命名空間中的類型 <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> 無法使用。

#### <a name="version-introduced"></a>引進的版本

.NET Core 3.0 Preview 8

#### <a name="change-description"></a>變更描述

命名空間中的類型 <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> 可在某些 .Net Core 3.0 預覽版本中使用。 從 .NET Core 3.0 Preview 9 開始就不再提供這些功能。

已移除類型，以避免不必要的元件相依性或後續版本中的重大變更。

#### <a name="recommended-action"></a>建議的動作

如果您的程式碼相依于 <xref:Microsoft.VisualBasic.ApplicationServices> 類型及其成員的使用，您可以在 .net 類別庫中使用對應的類型或成員。 例如，某些 <xref:System.Environment?displayProperty=nameWithType> 和 <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> 成員會提供對等的功能給類別的屬性 <xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType> 。

#### <a name="category"></a>類別

Visual Basic

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.ApplicationServices`

-->
