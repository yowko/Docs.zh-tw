---
title: "System.Transactions 與 SQL Server 整合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 21924441c091c53a79d4b7bf8a683f8a7c74bd07
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="systemtransactions-integration-with-sql-server"></a>System.Transactions 與 SQL Server 整合
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 版導入了新的交易架構，可透過 <xref:System.Transactions> 命名空間 (Namespace) 進行存取。 此架構以完全整合到 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (包括 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]) 中的方式來公開交易。  
  
 除了增強程式設計之外，在處理交易時， <xref:System.Transactions> 還會與 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 一起運作協調出最佳效能。 可提升的交易是可視需要自動提升為完全分散式交易的輕量型 (本機) 交易。  
  
 從 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 開始， <xref:System.Data.SqlClient> 便支援在您使用 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]時進行可提升交易。 除非需要已加入的負荷，否則可提升交易不會叫用分散式交易的已加入負荷。 可提升異動是自動的而且需要無需開發人員從中操作。  
  
 只有 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server (`SqlClient`) 與 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]搭配使用時，才能使用可提升交易。  
  
## <a name="creating-promotable-transactions"></a>建立可提升交易  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provider for SQL Server 支援可提升交易，可透過 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <xref:System.Transactions> 命名空間中的類別來處理這些交易。 可提升交易藉由直到需要時才建立分散式交易的方式，來最佳化分散式交易。 如果只需要一個資源管理員，則不會發生分散式交易。  
  
> [!NOTE]
>  在部分信任案例中，當某筆交易提升至分散式交易時， <xref:System.Transactions.DistributedTransactionPermission> 就是必要項目。  
  
## <a name="promotable-transaction-scenarios"></a>可提升交易案例  
 分散式交易通常要耗用大量的系統資源，並由「Microsoft 分散式交易協調器 (MS DTC)」進行管理，其整合了交易中會存取的所有資源管理者。 可提升交易是 <xref:System.Transactions> 交易的特殊形式，可有效地委派工作給簡單的 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 交易。 <xref:System.Transactions>、 <xref:System.Data.SqlClient>及 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 會協調處理交易時所涉及的工作，並視需要將其提升為完全分散式交易。  
  
 使用可提升交易的好處是：當以作用中的 <xref:System.Transactions.TransactionScope> 交易開啟連接，且未開啟其他連接時，會將交易認可為輕量型交易，不會產生完全分散式交易的額外負擔。  
  
### <a name="connection-string-keywords"></a>連接字串關鍵字  
 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 屬性支援關鍵字 `Enlist`，它表示 <xref:System.Data.SqlClient> 是否會偵測到交易內容，並自動在分散式交易中登記連接。 如果 `Enlist=true`，則會在開啟之執行緒的目前交易內容中自動登記連接。 如果 `Enlist=false`，則 `SqlClient` 連接將不會與分散式交易進行互動。 `Enlist` 的預設值為 True。 如果未在連接字串中指定 `Enlist` ，則若在開啟連接時偵測到連接，便會自動在分散式交易中登記該連接。  
  
 在 `Transaction Binding` 連接字串中的 <xref:System.Data.SqlClient.SqlConnection> 關鍵字會控制連接與已登記 `System.Transactions` 交易之間的關聯。 這也可以透過 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> 的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder>屬性取得。  
  
 下表說明可能出現的值。  
  
|關鍵字|描述|  
|-------------|-----------------|  
|Implicit Unbind|預設值。 結束時，連接會與交易中斷連結，並切換回自動認可模式。|  
|Explicit Unbind|連接會維持附加至交易的狀態，直到交易關閉為止。 如果相關聯的交易並非使用中或與 <xref:System.Transactions.Transaction.Current%2A>不符，連接將會失敗。|  
  
## <a name="using-transactionscope"></a>使用 TransactionScope  
 <xref:System.Transactions.TransactionScope> 類別可藉由在分散式交易中隱含地登記連接，來使程式碼區塊可進行交易。 離開區塊之前，您必須呼叫 <xref:System.Transactions.TransactionScope.Complete%2A> 區塊結尾的 <xref:System.Transactions.TransactionScope> 方法。 離開區塊會叫用 <xref:System.Transactions.TransactionScope.Dispose%2A> 方法。 如果已擲回造成程式碼離開範圍的例外狀況，則會將交易視為中止。  
  
 建議您使用 `using` 區塊，以確保結束 using 區塊時，會在 <xref:System.Transactions.TransactionScope.Dispose%2A> 物件上呼叫 <xref:System.Transactions.TransactionScope> 。 無法認可或復原暫止的交易會嚴重損害效能，因為 default time-out for the <xref:System.Transactions.TransactionScope> 的預設逾時是 1 分鐘。 如果您不使用 `using` 陳述式，則必須在 `Try` 區塊中執行所有工作，並明確呼叫 <xref:System.Transactions.TransactionScope.Dispose%2A> 區塊中的 `Finally` 方法。  
  
 如果 <xref:System.Transactions.TransactionScope>中發生例外狀況，則會將交易標記為不一致並放棄。 處置 <xref:System.Transactions.TransactionScope> 時，則會復原該交易。 如果沒有發生任何例外狀況，則會認可參與的交易。  
  
> [!NOTE]
>  根據預設， `TransactionScope` 類別會建立其 <xref:System.Transactions.Transaction.IsolationLevel%2A> 為 `Serializable` 的交易。 根據應用程式，您可能會考慮降低隔離等級，以避免應用程式中發生劇烈的爭用現象。  
  
> [!NOTE]
>  建議您在分散式交易內僅執行更新、插入及刪除作業，因為它們會耗用大量的資料庫資源。 SELECT 陳述式可能會不必要地鎖定資料庫資源，而在某些案例中，您可能需要使用交易而不是選取。 除非涉及其他已交易的資源管理者，否則所有非資料庫工作都應在交易範圍外執行。 雖然交易範圍內的例外狀況會防止認可交易，但 <xref:System.Transactions.TransactionScope> 類別不支援針對在交易本身範圍外所做的任何程式碼變更進行復原。 如果在復原交易時需要採取某些動作，則必須撰寫您自己的 <xref:System.Transactions.IEnlistmentNotification> 介面實作，並在交易中明確登記。  
  
## <a name="example"></a>範例  
 您需要參考 System.Transactions.dll，才能使用 <xref:System.Transactions> 。  
  
 下列函式示範如何針對由兩個不同的 <xref:System.Data.SqlClient.SqlConnection> 物件表示，並包裝於 <xref:System.Transactions.TransactionScope> 區塊中的兩個不同 SQL Server 執行個體，建立可提升交易。 程式碼會使用 <xref:System.Transactions.TransactionScope> 陳述式來建立 `using` 區塊，並開啟第一個連接，這樣會自動在 <xref:System.Transactions.TransactionScope>中登記它。 一開始交易登記為輕量型交易，而不是完全分散式交易。 只有當第一個連接中的命令沒有擲回例外狀況時，第二個連接才會登記於 <xref:System.Transactions.TransactionScope> 中。 開啟第二個連接時，交易會自動提升為完全分散式交易。 此時，系統會叫用 <xref:System.Transactions.TransactionScope.Complete%2A> 方法，但是它只有在沒有擲回任何例外狀況時才會認可交易。 如果在 <xref:System.Transactions.TransactionScope> 區塊中的任何一點擲回例外狀況，便不會呼叫 `Complete` ，且分散式交易會在 <xref:System.Transactions.TransactionScope> 區塊結束並處置 `using` 時復原。  
  
```csharp  
// This function takes arguments for the 2 connection strings and commands in order  
// to create a transaction involving two SQL Servers. It returns a value > 0 if the  
// transaction committed, 0 if the transaction rolled back. To test this code, you can   
// connect to two different databases on the same server by altering the connection string,  
// or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
static public int CreateTransactionScope(  
    string connectString1, string connectString2,  
    string commandText1, string commandText2)  
{  
    // Initialize the return value to zero and create a StringWriter to display results.  
    int returnValue = 0;  
    System.IO.StringWriter writer = new System.IO.StringWriter();  
  
    // Create the TransactionScope in which to execute the commands, guaranteeing  
    // that both commands will commit or roll back as a single unit of work.  
    using (TransactionScope scope = new TransactionScope())  
    {  
        using (SqlConnection connection1 = new SqlConnection(connectString1))  
        {  
            try  
            {  
                // Opening the connection automatically enlists it in the   
                // TransactionScope as a lightweight transaction.  
                connection1.Open();  
  
                // Create the SqlCommand object and execute the first command.  
                SqlCommand command1 = new SqlCommand(commandText1, connection1);  
                returnValue = command1.ExecuteNonQuery();  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue);  
  
                // if you get here, this means that command1 succeeded. By nesting  
                // the using block for connection2 inside that of connection1, you  
                // conserve server and network resources by opening connection2   
                // only when there is a chance that the transaction can commit.     
                using (SqlConnection connection2 = new SqlConnection(connectString2))  
                    try  
                    {  
                        // The transaction is promoted to a full distributed  
                        // transaction when connection2 is opened.  
                        connection2.Open();  
  
                        // Execute the second command in the second database.  
                        returnValue = 0;  
                        SqlCommand command2 = new SqlCommand(commandText2, connection2);  
                        returnValue = command2.ExecuteNonQuery();  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue);  
                    }  
                    catch (Exception ex)  
                    {  
                        // Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue);  
                        writer.WriteLine("Exception Message2: {0}", ex.Message);  
                    }  
            }  
            catch (Exception ex)  
            {  
                // Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue);  
                writer.WriteLine("Exception Message1: {0}", ex.Message);  
            }  
        }  
  
        // If an exception has been thrown, Complete will not   
        // be called and the transaction is rolled back.  
        scope.Complete();  
    }  
  
    // The returnValue is greater than 0 if the transaction committed.  
    if (returnValue > 0)  
    {  
        writer.WriteLine("Transaction was committed.");  
    }  
    else  
    {  
        // You could write additional business logic here, notify the caller by  
        // throwing a TransactionAbortedException, or log the failure.  
        writer.WriteLine("Transaction rolled back.");  
    }  
  
    // Display messages.  
    Console.WriteLine(writer.ToString());  
  
    return returnValue;  
}  
```  
  
```vb  
' This function takes arguments for the 2 connection strings and commands in order  
' to create a transaction involving two SQL Servers. It returns a value > 0 if the  
' transaction committed, 0 if the transaction rolled back. To test this code, you can   
' connect to two different databases on the same server by altering the connection string,  
' or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
Public Function CreateTransactionScope( _  
  ByVal connectString1 As String, ByVal connectString2 As String, _  
  ByVal commandText1 As String, ByVal commandText2 As String) As Integer  
  
    ' Initialize the return value to zero and create a StringWriter to display results.  
    Dim returnValue As Integer = 0  
    Dim writer As System.IO.StringWriter = New System.IO.StringWriter  
  
    ' Create the TransactionScope in which to execute the commands, guaranteeing  
    ' that both commands will commit or roll back as a single unit of work.  
    Using scope As New TransactionScope()  
        Using connection1 As New SqlConnection(connectString1)  
            Try  
                ' Opening the connection automatically enlists it in the   
                ' TransactionScope as a lightweight transaction.  
                connection1.Open()  
  
                ' Create the SqlCommand object and execute the first command.  
                Dim command1 As SqlCommand = New SqlCommand(commandText1, connection1)  
                returnValue = command1.ExecuteNonQuery()  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue)  
  
                ' If you get here, this means that command1 succeeded. By nesting  
                ' the Using block for connection2 inside that of connection1, you  
                ' conserve server and network resources by opening connection2   
                ' only when there is a chance that the transaction can commit.     
                Using connection2 As New SqlConnection(connectString2)  
                    Try  
                        ' The transaction is promoted to a full distributed  
                        ' transaction when connection2 is opened.  
                        connection2.Open()  
  
                        ' Execute the second command in the second database.  
                        returnValue = 0  
                        Dim command2 As SqlCommand = New SqlCommand(commandText2, connection2)  
                        returnValue = command2.ExecuteNonQuery()  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue)  
  
                    Catch ex As Exception  
                        ' Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue)  
                        writer.WriteLine("Exception Message2: {0}", ex.Message)  
                    End Try  
                End Using  
  
            Catch ex As Exception  
                ' Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue)  
                writer.WriteLine("Exception Message1: {0}", ex.Message)  
            End Try  
        End Using  
  
        ' If an exception has been thrown, Complete will   
        ' not be called and the transaction is rolled back.  
        scope.Complete()  
    End Using  
  
    ' The returnValue is greater than 0 if the transaction committed.  
    If returnValue > 0 Then  
        writer.WriteLine("Transaction was committed.")  
    Else  
        ' You could write additional business logic here, notify the caller by  
        ' throwing a TransactionAbortedException, or log the failure.  
       writer.WriteLine("Transaction rolled back.")  
     End If  
  
    ' Display messages.  
    Console.WriteLine(writer.ToString())  
  
    Return returnValue  
End Function  
```  
  
## <a name="see-also"></a>請參閱  
 [異動和並行存取](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
