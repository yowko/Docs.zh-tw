---
title: 本機異動
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ae3712f-ef5e-41a1-9ea9-b3d0399439f1
ms.openlocfilehash: a0cb72913c10712ece188a782095b93f98cdc0b2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955777"
---
# <a name="local-transactions"></a>本機異動
當您想要將多個工作系結在一起, 使其以單一工作單位的形式執行時, 會使用 ADO.NET 中的交易。 例如，想像應用程式正在執行兩項工作。 首先，它會更新包含訂單資訊的資料表。 然後會更新包含存貨資訊的資料表，將訂購項目記入借方。 如果其中一項工作失敗, 則會復原這兩個更新。  
  
## <a name="determining-the-transaction-type"></a>決定異動類型  
 當交易為單一階段交易時, 就會將其視為本機交易, 並直接由資料庫處理。 當交易由交易監視器協調並使用不安全的機制 (例如兩階段認可) 進行交易解析時, 就會將其視為分散式交易。  
  
 每個 .NET Framework 資料提供者都有自己`Transaction`的物件, 可執行本機交易。 如果您需要在 SQL Server 資料庫中執行異動，請選擇 <xref:System.Data.SqlClient> 異動。 若為 Oracle 異動，請使用 <xref:System.Data.OracleClient> 提供者。 此外, 還有一個<xref:System.Data.Common.DbTransaction>類別, 可以用來撰寫需要交易的提供者獨立程式碼。  
  
> [!NOTE]
> 當交易在伺服器上執行時, 最有效率。 如果您使用的 SQL Server 資料庫大量使用明確的異動，請考慮使用 Transact-SQL BEGIN TRANSACTION 陳述式，將它們寫入為預存程序。
  
## <a name="performing-a-transaction-using-a-single-connection"></a>使用單一連接執行異動  
 在 ADO.NET 中, 您可以使用`Connection`物件來控制交易。 您可使用 `BeginTransaction` 方法來起始本機異動。 開始異動之後，您可使用 `Transaction` 物件的 `Command` 屬性，在該異動中登記命令。 然後，您可根據異動元件的成敗，來認可或復原對資料來源所做的修改。  
  
> [!NOTE]
> `EnlistDistributedTransaction` 方法不可用於本機異動。  
  
 交易的範圍僅限於連接。 下列範例執行由 `try` 區塊中的兩個單獨命令所組成的明確異動。 這些命令會針對 AdventureWorks SQL Server 範例資料庫中的 Production.scrapreason 資料表執行 INSERT 語句, 如果未擲回任何例外狀況, 則會認可。 如果擲回例外狀況，則 `catch` 區塊中的程式碼便會復原交易。 如果異動在完成之前遭到中止或連接關閉，則會自動復原該異動。  
  
## <a name="example"></a>範例  
 請遵循下列步驟來執行異動。  
  
1. 呼叫 <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> 物件的 <xref:System.Data.SqlClient.SqlConnection> 方法，來標記交易的開始。 <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> 方法會將參考傳回給交易。 此參考會指派給登記在交易中的 <xref:System.Data.SqlClient.SqlCommand> 物件。  
  
2. 將 `Transaction` 物件指派給要執行之 <xref:System.Data.SqlClient.SqlCommand.Transaction%2A> 的 <xref:System.Data.SqlClient.SqlCommand> 屬性。 如果在有異動正在作用中的連接上執行命令，且 `Transaction` 物件尚未指派給 `Transaction` 物件的 `Command` 屬性，便會擲回例外狀況。  
  
3. 執行必要的命令。  
  
4. 呼叫 <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> 物件的 <xref:System.Data.SqlClient.SqlTransaction> 方法來完成交易，或呼叫 <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> 方法來中止交易。 如果在執行 <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> 或 <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> 方法之前關閉或處置連接，則會復原異動。  
  
 下列程式碼範例示範使用 ADO.NET 搭配 Microsoft SQL Server 的交易式邏輯。  
  
 [!code-csharp[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [異動和並行存取](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [分散式異動](../../../../docs/framework/data/adonet/distributed-transactions.md)
- [System.Transactions 與 SQL Server 整合](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
