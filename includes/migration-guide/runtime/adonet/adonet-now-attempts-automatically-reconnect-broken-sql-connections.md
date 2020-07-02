---
ms.openlocfilehash: 23ba6064a283b47312a66f3636c2834a7d58106e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619946"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a>ADO.NET 現在會嘗試自動重新連接中斷的 SQL 連線

#### <a name="details"></a>詳細資料

從 .NET Framework 4.5.1 中開始，.NET Framework 將嘗試自動重新連接中斷的 SQL 連線。 雖然這通常會讓應用程式更可靠，但是會有邊緣案例，應用程式必須知道連線已中斷，讓它可以在重新連接時採取某些動作。

#### <a name="suggestion"></a>建議

如果基於相容性考量，您不想要這項功能，可以將連接字串的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> 屬性 (或 <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) 設為 0 來加以停用。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.5.1|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)></li></ul>|
