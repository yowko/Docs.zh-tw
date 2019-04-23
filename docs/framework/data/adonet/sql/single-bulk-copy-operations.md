---
title: 單一大量複製作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: b2783779965505d09f73c7203770c19ccaa78d26
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59323365"
---
# <a name="single-bulk-copy-operations"></a>單一大量複製作業
執行 SQL Server 大量複製作業的最簡單方法是：針對資料庫執行單一作業。 根據預設，會以隔離作業執行大量複製作業：複製作業會以非交易性方式執行，且沒有復原的機會。  
  
> [!NOTE]
>  如果需要在發生錯誤時，復原全部或部分大量複製，您可以使用 <xref:System.Data.SqlClient.SqlBulkCopy> 管理的交易，或在現有交易內執行大量複製作業。 **SqlBulkCopy**也適用於<xref:System.Transactions>如果將連接登記 （隱含或明確） 成**System.Transactions**交易。  
>   
>  如需詳細資訊，請參閱 <<c0> [ 異動和大量複製作業](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)。  
  
 執行大量複製作業的一般步驟如下：  
  
1. 連接至來源伺服器，並取得要複製的資料。 如果可從 <xref:System.Data.IDataReader> 或 <xref:System.Data.DataTable> 物件擷取資料，則資料也可來自其他來源。  
  
2. 連接到目的地伺服器 (除非您想**SqlBulkCopy**為您建立的連線)。  
  
3. 建立 <xref:System.Data.SqlClient.SqlBulkCopy> 物件，設定所有必要的屬性。  
  
4. 設定**DestinationTableName**屬性來指定目標資料表，進行大量插入作業。  
  
5. 呼叫其中一種**WriteToServer**方法。  
  
6. （選擇性） 更新屬性，並呼叫**WriteToServer**視一次。  
  
7. 呼叫 <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>，或將大量複製作業包裝至 `Using` 陳述式內。  
  
> [!CAUTION]
>  建議來源與目標資料行的資料型別相符。 如果不相符的資料類型， **SqlBulkCopy**會嘗試將每個來源值轉換成目標資料類型，使用所採用的規則<xref:System.Data.SqlClient.SqlParameter.Value%2A>。 轉換可能會影響效能，亦可能導致意外的錯誤。 例如，`Double` 資料型別通常可轉換為 `Decimal` 資料型別，但並非始終如此。  
  
## <a name="example"></a>範例  
 下列主控台應用程式示範如何使用 <xref:System.Data.SqlClient.SqlBulkCopy> 類別來載入資料。 在此範例中，<xref:System.Data.SqlClient.SqlDataReader>用來複製資料，從**Production.Product** SQL Server 中的表格**AdventureWorks**相同資料庫中的類似資料表的資料庫。  
  
> [!IMPORTANT]
>  此範例不會執行，除非您已建立的工作資料表中所述[大量複製範例設定](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)。 此程式碼可示範使用語法**SqlBulkCopy**只。 如果來源及目的地資料表位於相同的 SQL Server 執行個體中，則使用 Transact-SQL `INSERT … SELECT` 陳述式來複製資料會更方便且快速。  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>使用 Transact-SQL 及命令類別來執行大量複製作業  
 下列範例說明如何使用 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> 方法執行 BULK INSERT 陳述式。  
  
> [!NOTE]
>  資料來源的檔案路徑是與伺服器相對的。 伺服器處理序必須存取該路徑，才能順利完成大量複製作業。  
  
```vb  
Using connection As SqlConnection = New SqlConnection(connectionString)  
Dim queryString As String = _  
    "BULK INSERT Northwind.dbo.[Order Details] FROM " & _  
    "'f:\mydata\data.tbl' WITH (FORMATFILE='f:\mydata\data.fmt' )"  
connection.Open()  
SqlCommand command = New SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery()  
End Using  
```  
  
```csharp  
using (SqlConnection connection = New SqlConnection(connectionString))  
{  
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +  
    "FROM 'f:\mydata\data.tbl' " +  
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";  
connection.Open();  
SqlCommand command = new SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery();  
}  
```  
  
## <a name="see-also"></a>另請參閱

- [在 SQL Server 中執行大量複製作業](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
