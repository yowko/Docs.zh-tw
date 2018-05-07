---
title: SQL Server 的提供者統計資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: f32b1c9f800a1ec2d80511cbbf46aba9840075d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="provider-statistics-for-sql-server"></a>SQL Server 的提供者統計資料
從 .NET Framework 2.0 版開始，.NET Framework Data Provider for SQL Server 便支援執行階段統計資料。 建立有效的連接物件後，您必須藉由將 <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> 物件的 <xref:System.Data.SqlClient.SqlConnection> 屬性設為 `True`，以啟用統計資料。 統計資料啟用後，透過 <xref:System.Collections.IDictionary> 物件的 <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> 方法擷取 <xref:System.Data.SqlClient.SqlConnection> 參考，可以將它們做為「某時間的快照集」進行檢閱。 您可使用一組名稱/值配對字典項目的形式透過清單列舉。 這些名稱/值配對沒有排列順序。 您可以隨時呼叫 <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> 物件的 <xref:System.Data.SqlClient.SqlConnection> 方法，以重設計數器。 如果尚未啟用統計資料蒐集，則不會產生例外狀況。 此外，如果呼叫 <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> 時未先呼叫 <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A>，則擷取的值會是每個項目的初始值。 如果啟用統計資料，並執行應用程式一段時間，然後停用統計資料，則擷取的值會反映到停用統計資料時所收集的值。 蒐集的所有統計資料值都是以每個連接為基礎。  
  
## <a name="statistical-values-available"></a>可用的統計值  
 Microsoft SQL Server 提供者目前有 18 個不同的可用項目。 可以透過可用的項目數目**計數**屬性<xref:System.Collections.IDictionary>介面所傳回的參考<xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>。 提供者統計資料計數器的所有使用 common language runtime<xref:System.Int64>類型 (**長**在 C# 和 Visual Basic 中)，這是 64 位元寬。 最大值**int64**資料類型所定義的**int64。MaxValue**欄位中，為 ((2^63) 1))。 計數器的值達到此最大值時，則不應再將其視為精確值。 這表示**int64。MaxValue**-1((2^63)-2) 實際上就是任何統計資料的最大有效值。  
  
> [!NOTE]
>  因為傳回之統計資料的數目、名稱及順序將來可能會變更，所以會使用字典來傳回提供者統計資料。 應用程式不應依賴在字典中發現的特定值，而應檢查該值是否存在，並相應地進行分支。  
  
 下表說明目前可用的統計值。 請注意，個別值的索引鍵名稱並未在 Microsoft .NET Framework 的區域版本中當地語系化。  
  
|索引鍵名稱|描述|  
|--------------|-----------------|  
|`BuffersReceived`|傳回在應用程式已開始使用提供者並啟用統計資料後，提供者從 SQL Server 接收之表格式資料流 (TDS) 封包的數目。|  
|`BuffersSent`|傳回在已啟用統計資料後，提供者傳送到 SQL Server 的 TDS 封包數目。 較大的命令會需要多個緩衝區。 例如，如果將較大的命令傳送至伺服器且其需要六個封包，則 `ServerRoundtrips` 數目會遞增一，而 `BuffersSent` 數目會遞增六。|  
|`BytesReceived`|傳回在應用程式已開始使用提供者並啟用統計資料後，提供者從 SQL Server 接收之 TDS 封包中的資料位元組數目。|  
|`BytesSent`|傳回在應用程式已開始使用提供者並啟用統計資料後，TDS 封包中傳送至 SQL Server 之資料的位元組數目。|  
|`ConnectionTime`|在啟用統計資料後連接已開啟的時間量 (以毫秒為單位；如果統計資料是在開啟連接之前啟用的，則為總連接時間)。|  
|`CursorOpens`|一旦應用程式已開始使用提供者並啟用統計資料後，傳回透過連接開啟游標的次數。<br /><br /> 請注意，不會將 SELECT 陳述式傳回的唯讀/順向結果視為游標，因此不會影響此計數器。|  
|`ExecutionTime`|一旦啟用統計資料後，傳回提供者在處理作業所耗用的累計時間量 (以毫秒為單位)，包括等待伺服器回覆的時間，以及提供者自身執行程式碼的時間。<br /><br /> 包含執行時間程式碼的類別有：<br /><br /> SqlConnection<br /><br /> SqlCommand<br /><br /> SqlDataReader<br /><br /> SqlDataAdapter<br /><br /> SqlTransaction<br /><br /> SqlCommandBuilder<br /><br /> 為了讓對效能有關鍵作用的成員數目儘可能最小，不會對下列成員計時：<br /><br /> SqlDataReader<br /><br /> this[] 運算子 (全部多載)<br /><br /> GetBoolean<br /><br /> GetChar<br /><br /> GetDateTime<br /><br /> GetDecimal<br /><br /> GetDouble<br /><br /> GetFloat<br /><br /> GetGuid<br /><br /> GetInt16<br /><br /> GetInt32<br /><br /> GetInt64<br /><br /> GetName<br /><br /> GetOrdinal<br /><br /> GetSqlBinary<br /><br /> GetSqlBoolean <br /><br /> GetSqlByte <br /><br /> GetSqlDateTime <br /><br /> GetSqlDecimal <br /><br /> GetSqlDouble <br /><br /> GetSqlGuid <br /><br /> GetSqlInt16 <br /><br /> GetSqlInt32 <br /><br /> GetSqlInt64 <br /><br /> GetSqlMoney <br /><br /> GetSqlSingle <br /><br /> GetSqlString <br /><br /> GetString<br /><br /> IsDBNull|  
|`IduCount`|一旦應用程式已開始使用提供者並啟用統計資料後，傳回透過連接執行之 INSERT、DELETE 及 UPDATE 陳述式的總數。|  
|`IduRows`|一旦應用程式已開始使用提供者並啟用統計資料後，傳回透過連接執行的 INSERT、DELETE 及 UPDATE 陳述式所影響的資料列總數。|  
|`NetworkServerTime`|一旦應用程式已開始使用提供者並啟用統計資料後，傳回提供者等待伺服器回覆的累計時間量 (以毫秒為單位)。|  
|`PreparedExecs`|一旦應用程式已開始使用提供者並啟用統計資料後，傳回透過連接執行之預備命令的數目。|  
|`Prepares`|一旦應用程式已開始使用提供者並啟用統計資料後，傳回透過連接預備的陳述式數目。|  
|`SelectCount`|一旦應用程式已開始使用提供者並啟用統計資料後，傳回透過連接執行之 SELECT 陳述式的數目。 這包含從游標擷取資料列的 FETCH 陳述式，且會在達到 <xref:System.Data.SqlClient.SqlDataReader> 的結尾時更新 SELECT 陳述式的計數。|  
|`SelectRows`|一旦應用程式已開始使用提供者並啟用統計資料後，傳回選取的資料列數目。 此計數器會反映 SQL 陳述式產生的所有資料列，甚至包含呼叫端實際上並未使用的資料列。 例如，在讀取整個結果集之前關閉資料讀取器不會影響計數。 這會包含透過 FETCH 陳述式從游標擷取的資料列。|  
|`ServerRoundtrips`|一旦應用程式已開始使用提供者並啟用統計資料後，傳回連接傳送命令至伺服器並取得回覆的次數。|  
|`SumResultSets`|一旦應用程式已開始使用提供者並啟用統計資料後，傳回已使用的結果集數目。 例如，這會包含傳回至用戶端的任何結果集。 對於游標，會將每個擷取或封鎖擷取作業視為獨立的結果集。|  
|`Transactions`|一旦應用程式已開始使用提供者並啟用統計資料後，傳回已啟動的使用者交易數目，包括復原。 如果連接執行時已啟用自動認可，則會將每個命令視為交易。<br /><br /> 一旦執行 BEGIN TRAN 陳述式，此計數器便會遞增交易計數，而不論是否會認可或稍後復原交易。|  
|`UnpreparedExecs`|一旦應用程式已開始使用提供者並啟用統計資料後，傳回透過連接執行之取消準備的陳述式數目。|  
  
### <a name="retrieving-a-value"></a>擷取值  
 下列主控台應用程式會顯示如何在連接上啟用統計資料、如何擷取四個個別的統計資料值，以及如何將它們寫入至主控台視窗。  
  
> [!NOTE]
>  下列範例使用範例**AdventureWorks**隨附於 SQL Server 資料庫。 範例程式碼中提供的連接字串假設本機電腦已安裝並可使用資料庫。 視環境需要修改連接字串。  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrive it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =   
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrive it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a>擷取所有值  
 下列主控台應用程式會顯示如何在連接上啟用統計資料、如何使用列舉值擷取所有可用的統計資料值，以及如何將它們寫入至主控台視窗。  
  
> [!NOTE]
>  下列範例使用範例**AdventureWorks**隨附於 SQL Server 資料庫。 範例程式碼中提供的連接字串假設本機電腦已安裝並可使用資料庫。 視環境需要修改連接字串。  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrive it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrive it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server 和 ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
