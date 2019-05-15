---
title: ADO.NET 的新功能
ms.date: 03/30/2017
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
ms.openlocfilehash: b54f7ab6505f86d0447654f21b197644d68254c0
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583444"
---
# <a name="whats-new-in-adonet"></a>ADO.NET 的新功能

下列功能是 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 中 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] 的新功能。

## <a name="sqlclient-data-provider"></a>SqlClient Data Provider

在.NET Framework Data Provider for SQL Server 中的新功能如下[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]:

- ConnectRetryCount 和 ConnectRetryInterval 連接字串關鍵字 (<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>) 可讓您控制閒置連接恢復功能。

- 資料流的應用程式從 SQL Server 支援可支援資料在伺服器上的非結構化的案例。  請參閱[SqlClient 資料流支援](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)如需詳細資訊。

- 增加對非同步程式設計的支援。  請參閱[非同步程式設計](../../../../docs/framework/data/adonet/asynchronous-programming.md)如需詳細資訊。

- 現在會將連接失敗記錄在擴充事件記錄中。 如需詳細資訊，請參閱 [ADO.NET 中的資料追蹤](../../../../docs/framework/data/adonet/data-tracing.md)。

- SqlClient 現在會提供對於 SQL Server 的高可用性、 災害復原功能，AlwaysOn 的支援。 如需詳細資訊，請參閱 <<c0> [ 高可用性、 嚴重損壞修復的 SqlClient 支援](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md)。

- 密碼可以當做<xref:System.Security.SecureString>時使用 SQL Server 驗證。 如需詳細資訊，請參閱 <xref:System.Data.SqlClient.SqlCredential>。

- 當`TrustServerCertificate`為 false 和`Encrypt`為 true，在 SQL Server SSL 憑證中的伺服器名稱 （或 IP 位址） 必須完全符合的伺服器名稱 （或 IP 位址） 連接字串中指定。 否則連接嘗試會失敗。 如需詳細資訊，請參閱 `Encrypt` 中有關 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 連線選項的說明。

  如果此變更導致現有的應用程式不再連線，您可以使用下列其中一種方法修復應用程式：

  - 簽發在 [一般名稱] \(CN) 或 [主體別名] \(SAN) 欄位中指定簡短名稱的憑證。 此解決方法適用於資料庫鏡像。

  - 加入別名，將簡短名稱對應至完整網域名稱。

  - 在連接字串中使用完整網域名稱。

- SqlClient 支援延伸的保護。 如需有關擴充保護的詳細資訊，請參閱[連接到 Database Engine 使用擴充保護](https://go.microsoft.com/fwlink/?LinkId=219978)。

- SqlClient 支援連接至 LocalDB 資料庫。 如需詳細資訊，請參閱 < [LocalDB 的 SqlClient 支援](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-localdb.md)。

- `Type System Version=SQL Server 2012;` 是傳遞至 `Type System Version` 連接屬性的新值。 `Type System Version=Latest;` 值現在已過時，並與 `Type System Version=SQL Server 2008;` 相等。 如需詳細資訊，請參閱 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。

- SqlClient 提供額外的疏鬆資料行支援，這是在 SQL Server 2008 中新增的功能。 如果您的應用程式已存取使用疏鬆資料行之資料表中的資料，效能應該會有所提高。 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> 的 IsColumnSet 資料行指出資料行是否為屬於資料行集的疏鬆資料行。 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> 指出資料行是否為疏鬆資料行 (請參閱[SQL Server 結構描述集合](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)如需詳細資訊)。 如需有關疏鬆資料行的詳細資訊，請參閱 <<c0> [ 使用疏鬆資料行](https://go.microsoft.com/fwlink/?LinkId=224244)。

- 包含空間資料類型的 Microsoft.SqlServer.Types.dll 組件已從 10.0 版升級至 11.0 版。 參考此組件的應用程式可能會失敗。 如需詳細資訊，請參閱 < [Database Engine 功能的突破性變更](https://go.microsoft.com/fwlink/?LinkId=224367)。

## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework

[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] 新增應用程式開發介面，可在搭配使用 Entity Framework 5.0 時啟用新案例。 如需有關改善和已新增至 Entity Framework 5.0 的功能的詳細資訊，請參閱下列主題：[最新消息](https://go.microsoft.com/fwlink/?LinkID=251106)並[Entity Framework 版本與版本控制](https://go.microsoft.com/fwlink/?LinkId=234899)。

## <a name="see-also"></a>另請參閱

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [ADO.NET 概觀](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [SQL Server 和 ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)
- [WCF Data Services 5.0 中最新消息](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
