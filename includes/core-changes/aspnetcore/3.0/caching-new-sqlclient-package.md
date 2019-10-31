---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198383"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>快取： SqlClient 使用新的封裝

`Microsoft.Extensions.Caching.SqlServer` 套件將會使用新的 `Microsoft.Data.SqlClient` 套件，而不是 `System.Data.SqlClient` 套件。 這種變更可能會造成些許的行為重大變更。 如需詳細資訊，請參閱[新的 SqlClient 簡介](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`Microsoft.Extensions.Caching.SqlServer` 封裝使用了 `System.Data.SqlClient` 套件。

#### <a name="new-behavior"></a>新的行為

`Microsoft.Extensions.Caching.SqlServer` 現在正在使用 `Microsoft.Data.SqlClient` 套件。

#### <a name="reason-for-change"></a>變更的原因

`Microsoft.Data.SqlClient` 是建置於 `System.Data.SqlClient` 的新套件。 從現在開始，所有的新功能工作都將從這裡開始進行。

#### <a name="recommended-action"></a>建議的動作

除非客戶使用 `Microsoft.Extensions.Caching.SqlServer` 封裝所傳回的類型，並將它們轉換成 `System.Data.SqlClient` 類型，否則不應擔心這項重大變更。 例如，如果有人將 `DbConnection` 轉換成[舊的 SqlConnection 型](xref:System.Data.SqlClient.SqlConnection)別，則必須將轉換變更為新的 `Microsoft.Data.SqlClient.SqlConnection` 型別。

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
