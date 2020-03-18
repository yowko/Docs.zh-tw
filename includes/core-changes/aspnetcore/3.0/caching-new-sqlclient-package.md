---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198383"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>緩存：微軟.擴展.緩存.SqlServer 使用新的 SqlClient 包

包`Microsoft.Extensions.Caching.SqlServer`將使用新`Microsoft.Data.SqlClient`包而不是`System.Data.SqlClient`包。 此更改可能會導致輕微的行為中斷更改。 有關詳細資訊，請參閱[介紹新的 Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

包`Microsoft.Extensions.Caching.SqlServer`使用了包`System.Data.SqlClient`。

#### <a name="new-behavior"></a>新的行為

`Microsoft.Extensions.Caching.SqlServer`正在使用包`Microsoft.Data.SqlClient`。

#### <a name="reason-for-change"></a>更改原因

`Microsoft.Data.SqlClient`是 由 構建的新包`System.Data.SqlClient`。 從現在起，所有新功能工作都將在這裡完成。

#### <a name="recommended-action"></a>建議的動作

客戶無需擔心這種重大更改，除非他們使用`Microsoft.Extensions.Caching.SqlServer`包返回的類型並將其強制轉換給`System.Data.SqlClient`類型。 例如，如果有人將 強制轉換為`DbConnection`[舊的 SqlConnection 類型](xref:System.Data.SqlClient.SqlConnection)，則需要將強制轉換更改為新`Microsoft.Data.SqlClient.SqlConnection`類型。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
