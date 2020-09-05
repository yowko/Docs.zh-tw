---
ms.openlocfilehash: c27c63e5bbd4a144b9482a0b1cb74250ae78d91c
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497129"
---
### <a name="connection-pool-blocking-period-for-azure-sql-databases-is-removed"></a>Azure SQL 資料庫的連線集區封鎖期已移除

#### <a name="details"></a>詳細資料

從 .NET Framework 4.6.2 開始，針對已知 Azure SQL 資料庫的連線開啟要求 (\* . database.windows.net、 \* database.chinacloudapi.cn、 \* database.usgovcloudapi.net、 \* database.cloudapi.de) 、已移除連接集區封鎖期間，且未快取連接開啟的錯誤。 發生暫時性連線錯誤之後，幾乎會立即嘗試重試連線開啟要求。 這項變更允許立即重試 Azure SQL Database 的連線開啟嘗試，因而提升啟用雲端功能的應用程式效能。 至於所有其他連線嘗試，則會繼續強制執行連線集區封鎖期。<p/>在 .NET Framework 4.6.1 和舊版中，如果應用程式在連線到資料庫時發生暫時性連線失敗，由於連線集區會快取此錯誤並在 5 秒鐘到 1 分鐘後重新擲回，因此無法很快就重試連線。 如需詳細資訊，請參閱 [SQL Server 連線共用 (ADO.NET)](~/docs/framework/data/adonet/sql-server-connection-pooling.md) \(機器翻譯\)。 此行為會對 Azure SQL Database 連線造成問題，連線通常會因暫時性錯誤而失敗，而且一般會在幾秒內復原。 連線集區封鎖功能表示應用程式有很長的一段時間無法連線到資料庫，即使資料庫可供使用且應用程式需要在幾秒內呈現也一樣。

#### <a name="suggestion"></a>建議

如果不需要這種行為，可以藉由設定 .NET Framework 4.6.2 中引進的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=fullName> 屬性來設定連線集區封鎖期。 屬性的值是 <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=fullName> 列舉的成員，可以採用三個值的其中一個值︰<ul><li><xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.Auto></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock></li></ul>將 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=fullName> 屬性設為 <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock> 可以還原舊有行為。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Minor|
|版本|4.6.2|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Data.Common.DbConnection.OpenAsync?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Data.Common.DbConnection.OpenAsync`
- `M:System.Data.SqlClient.SqlConnection.Open`
- `M:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)`

-->
