---
title: 新功能
ms.date: 03/30/2017
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
ms.openlocfilehash: 2ac8ebced700dc6c874ac22304773b3b9c19f8b3
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "76979763"
---
# <a name="whats-new-in-adonet"></a>ADO.NET 的新功能

下列是 .NET Framework 4.5 中 ADO.NET 的新功能。

## <a name="sqlclient-data-provider"></a>SqlClient Data Provider

以下是 .NET Framework 4.5 中 SQL Server 的 .NET Framework Data Provider 的新功能：

- ConnectRetryCount 和 ConnectRetryInterval 連接字串關鍵字 (<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>) 可讓您控制閒置連接恢復功能。

- 從 SQL Server 到應用程式的串流支援，支援伺服器上的資料是非結構化的案例。  如需詳細資訊，請參閱[SqlClient 串流支援](sqlclient-streaming-support.md)。

- 增加對非同步程式設計的支援。  如需詳細資訊，請參閱[非同步程式設計](asynchronous-programming.md)。

- 現在會將連接失敗記錄在擴充事件記錄中。 如需詳細資訊，請參閱 [ADO.NET 中的資料追蹤](data-tracing.md)。

- SqlClient 現在支援 SQL Server 的高可用性、嚴重損壞修復功能、AlwaysOn。 如需詳細資訊，請參閱[高可用性和嚴重損壞修復的 SqlClient 支援](./sql/sqlclient-support-for-high-availability-disaster-recovery.md)。

- 使用 SQL Server Authentication 時，密碼可以做為 <xref:System.Security.SecureString> 傳遞。 如需詳細資訊，請參閱 <xref:System.Data.SqlClient.SqlCredential>。

- 當 `TrustServerCertificate` 為 false 且 `Encrypt` 為 true 時，SQL Server SSL 憑證中的伺服器名稱（或 IP 位址）必須完全符合連接字串中指定的伺服器名稱（或 IP 位址）。 否則連接嘗試會失敗。 如需詳細資訊，請參閱 `Encrypt` 中有關 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 連線選項的說明。

  如果此變更導致現有的應用程式不再連線，您可以使用下列其中一種方法修復應用程式：

  - 簽發在 [一般名稱] (CN) 或 [主體別名] (SAN) 欄位中指定簡短名稱的憑證。 此解決方法適用於資料庫鏡像。

  - 加入別名，將簡短名稱對應至完整網域名稱。

  - 在連接字串中使用完整網域名稱。

- SqlClient 支援延伸的保護。 如需擴充保護的詳細資訊，請參閱[使用擴充保護連接到資料庫引擎](/sql/database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection)。

- SqlClient 支援連接至 LocalDB 資料庫。 如需詳細資訊，請參閱[SqlClient Support For LocalDB](./sql/sqlclient-support-for-localdb.md)。

- `Type System Version=SQL Server 2012;` 是傳遞至 `Type System Version` 連接屬性的新值。 `Type System Version=Latest;` 值現在已過時，並與 `Type System Version=SQL Server 2008;` 相等。 如需詳細資訊，請參閱<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。

- SqlClient 提供額外的疏鬆資料行支援，這是在 SQL Server 2008 中新增的功能。 如果您的應用程式已存取使用疏鬆資料行的資料表中之資料，應會看到效能有所提升。 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> 的 IsColumnSet 資料行指出資料行是否為屬於資料行集的疏鬆資料行。 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> 指出資料行是否為稀疏資料行（如需詳細資訊，請參閱[SQL Server 架構集合](sql-server-schema-collections.md)）。 如需稀疏資料行的詳細資訊，請參閱[使用稀疏資料行](/sql/relational-databases/tables/use-sparse-columns)。

- 包含空間資料類型的 Microsoft.SqlServer.Types.dll 組件已經從 10.0 版升級為 11.0 版。 參考此組件的應用程式可能會失敗。 如需詳細資訊，請參閱[資料庫引擎功能的重大變更](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/ms143179(v=sql.110))。

## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework

.NET Framework 4.5 會新增 Api，以在使用 Entity Framework 5.0 時啟用新的案例。 如需有關已新增至 Entity Framework 5.0 的改進功能和功能的詳細資訊，請參閱下列主題：[新功能](https://docs.microsoft.com/previous-versions/gg696190(v=vs.103))和[Entity Framework 版本和版本控制](/ef/ef6/what-is-new/past-releases)。

## <a name="see-also"></a>請參閱

- [ADO.NET](index.md)
- [ADO.NET 概觀](ado-net-overview.md)
- [SQL Server 和 ADO.NET](./sql/index.md)
- [5.0 WCF Data Services 的新功能](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))
