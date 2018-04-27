### <a name="connection-pool-blocking-period-for-azure-sql-databases-is-removed"></a>Azure SQL 資料庫的連線集區封鎖期已移除

|   |   |
|---|---|
|詳細資料|從.NET Framework 4.6.2 開始，連接開啟要求至已知的 Azure SQL 資料庫 (*.database.windows.net，*.database.chinacloudapi.cn，*.database.usgovcloudapi.net，*.database.cloudapi.de)，是封鎖期間內的連接集區移除，並不會快取連接開啟的錯誤。 發生暫時性連線錯誤之後，幾乎會立即嘗試重試連線開啟要求。 這項變更允許立即重試 Azure SQL Database 的連線開啟嘗試，因而提升啟用雲端功能的應用程式效能。 至於所有其他連線嘗試，則會繼續強制執行連線集區封鎖期。在 .NET Framework 4.6.1 和舊版中，如果應用程式在連線到資料庫時發生暫時性連線失敗，由於連線集區會快取此錯誤並在 5 秒鐘到 1 分鐘後重新擲回，因此無法很快就重試連線。 如需詳細資訊，請參閱 [SQL Server 連共用ADO.NET)](~/docs/framework/data/adonet/sql-server-connection-pooling.md)。 此行為會對 Azure SQL Database 連線造成問題，連線通常會因暫時性錯誤而失敗，而且一般會在幾秒內復原。 連線集區封鎖功能表示應用程式有很長的一段時間無法連線到資料庫，即使資料庫可供使用且應用程式需要在幾秒內呈現也一樣。|
|建議|如果不需要這種行為，可以藉由設定 .NET Framework 4.6.2 中引進的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> 屬性來設定連線集區封鎖期。 屬性的值是 <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=name> 列舉的成員，可以採用三個值的其中一個值︰<ul><li><xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.Auto></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock></li></ul>將 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> 屬性設為 <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock> 可以還原舊有行為。|
|範圍|次要|
|版本|4.6.2|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Data.Common.DbConnection.OpenAsync?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|

