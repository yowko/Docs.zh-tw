---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394177"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a>共用框架：刪除微軟.AspNetCore.所有

從 ASP.NET 酷 3.0`Microsoft.AspNetCore.All`開始，不再生成`Microsoft.AspNetCore.All`元包和匹配的共用框架。 此包在 ASP.NET 酷 2.2 中可用，並將繼續在 ASP.NET 酷 2.1 中接收服務更新。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

應用可以使用`Microsoft.AspNetCore.All`元包在 .NET `Microsoft.AspNetCore.All` Core 上定位共用框架。

#### <a name="new-behavior"></a>新的行為

.NET Core 3.0 不包括`Microsoft.AspNetCore.All`共用框架。

#### <a name="reason-for-change"></a>更改原因

元`Microsoft.AspNetCore.All`包包含大量外部依賴項。

#### <a name="recommended-action"></a>建議的動作

遷移專案以使用`Microsoft.AspNetCore.App`框架。 以前可用的元件`Microsoft.AspNetCore.All`在 NuGet 上仍然可用。 這些元件現在隨應用一起部署，而不是包含在共用框架中。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
