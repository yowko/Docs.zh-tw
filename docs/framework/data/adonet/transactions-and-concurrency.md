---
title: 異動和並行存取
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: c78031150d9b1209372dece49813dfcf0a03b9d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965218"
---
# <a name="transactions-and-concurrency"></a>異動和並行存取
異動是由單一命令或當做封裝 (Package) 執行的命令群組所組成。 交易可讓您將多項作業結合成單一工作單位。 如果異動的某一處失敗，則所有更新都會復原到異動之前的狀態。  
  
 異動必須符合 ACID 屬性 (單元性 (Atomicity)、一致性 (Consistency)、隔離性 (Isolation) 和持續性 (Durability)，才能保證資料一致性。 大多數關聯式資料庫系統 (例如 Microsoft SQL Server) 都可以支援異動，其方法是在每次用戶端應用程式執行更新、插入或刪除作業時，提供鎖定、記錄和異動管理功能。  
  
> [!NOTE]
> 如果鎖定保留時間太久，包含多個資源的交易可能會降低並行。 因此，請盡可能縮短異動的時間長度。  
  
 如果某筆異動包含相同資料庫或伺服器中的多個資料表，則預存程序 (Stored Procedure) 中的明確異動通常會有較佳的效能。 您可以使用 Transact-SQL `BEGIN TRANSACTION`、`COMMIT TRANSACTION` 和 `ROLLBACK TRANSACTION` 陳述式，在 SQL Server 預存程序中建立交易。 如需詳細資訊，請參閱《SQL Server 線上叢書》。  
  
 涉及不同資源管理員的交易 (例如 SQL Server 與 Oracle 之間的交易) 需要分散式交易。  
  
## <a name="in-this-section"></a>本節內容  
 [本機異動](../../../../docs/framework/data/adonet/local-transactions.md)  
 示範如何針對資料庫執行交易。  
  
 [分散式異動](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 說明如何在 ADO.NET 中執行分散式異動。  
  
 [System.Transactions 與 SQL Server 整合](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 描述<xref:System.Transactions>如何與使用分散式交易的 SQL Server 整合。  
  
 [開放式並行存取](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 說明開放式與封閉式同步存取，以及如何測試並行違規。  
  
## <a name="see-also"></a>另請參閱

- [交易基礎概念](../../../../docs/framework/data/transactions/transaction-fundamentals.md)
- [連接至資料來源](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
