---
title: 連接字串產生器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: a29efbc1b4d886afe4329df011b522e4d589e2ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949497"
---
# <a name="connection-string-builders"></a>連接字串產生器
在舊版的 ADO.NET 中, 不會發生具有串連字號串值之連接字串的編譯階段檢查, 因此在執行時間, 不正確的關鍵字會產生<xref:System.ArgumentException>。 .NET Framework 的每個資料提供者都支援不同的連接字串關鍵字語法, 這會在手動完成時, 讓建立有效的連接字串變得不容易。 為了解決這個問題, ADO.NET 2.0 為每個 .NET Framework Data Provider 引進了新的連接字串產生器。 每個資料提供者都具有繼承自 <xref:System.Data.Common.DbConnectionStringBuilder> 強型別連接字串產生器類別。 下表列出 .NET Framework 資料提供者及其相關聯的連接字串產生器類別。  
  
|提供者|ConnectionStringBuilder 類別|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a>連接字串插入式攻擊  
 當使用動態字串串連產生根據使用者輸入而來的連接字串時，就可能發生連接字串隱碼攻擊。 如果字串未經驗證且未逸出惡意的文字或字元，攻擊者就可能得以存取伺服器上的機密資料或其他資源。 例如，攻擊者可以藉由提供分號並附加額外的值而掛上 (Mount) 攻擊。 連接字串會受到「最後一個設定」演算法剖析，而惡意的輸入值會取代合法的值。  
  
 連接字串產生器類別的目的是排除不確定性，並可防止語法錯誤和安全性漏洞。 此類別所提供的方法和屬性都對應於每個資料提供者所允許的已知索引鍵/值配對。 每個類別都會維持固定的同義資料表 (Synonym) 集合，且可從同義資料表轉譯為相對應的已知索引鍵名稱。 系統將針對有效的索引鍵/值組執行檢查，無效的索引鍵/值組將擲回例外狀況 (Exception)。 此外，插入的值也會以安全的方式處理。  
  
 下列範例示範 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 如何針對 `Initial Catalog` 設定而處理插入的額外值。  
  
```vb  
Dim builder As New System.Data.SqlClient.SqlConnectionStringBuilder  
builder("Data Source") = "(local)"  
builder("Integrated Security") = True  
builder("Initial Catalog") = "AdventureWorks;NewValue=Bad"  
Console.WriteLine(builder.ConnectionString)  
```  
  
```csharp  
System.Data.SqlClient.SqlConnectionStringBuilder builder =  
  new System.Data.SqlClient.SqlConnectionStringBuilder();  
builder["Data Source"] = "(local)";  
builder["integrated Security"] = true;  
builder["Initial Catalog"] = "AdventureWorks;NewValue=Bad";  
Console.WriteLine(builder.ConnectionString);  
```  
  
 輸出顯示上述情況的正確處理方式：<xref:System.Data.SqlClient.SqlConnectionStringBuilder> 以雙引號溢出額外值，而非以新的索引鍵/值組將該值附加到連接字串。  
  
```  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a>從組態檔建置連接字串  
 如果事先知道連接字串的特定項目，就可以先將其儲存在組態檔中，執行階段時再進行擷取，用以建構完整的連接字串。 例如，您可能會預先知道資料庫的名稱，但不知道伺服器的名稱； 或者，也可以讓使用者在執行階段提供名稱和密碼，但不能將其他值插入連接字串。  
  
 連接字串產生器其中一個多載建構函式會採用 <xref:System.String> 做為引數，這可讓您先提供部分連接字串，然後藉由使用者輸入完成。 部分連接字串可以儲存在組態檔中，並在執行階段進行擷取。  
  
> [!NOTE]
> <xref:System.Configuration> 命名空間可讓您以程式設計方式存取使用 <xref:System.Web.Configuration.WebConfigurationManager> (Web 應用程式) 和 <xref:System.Configuration.ConfigurationManager> (Windows 應用程式) 的組態檔。 如需使用連接字串和設定檔的詳細資訊, 請參閱[連接字串和設定檔](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)。  
  
### <a name="example"></a>範例  
 這個範例示範如何從組態檔擷取部分的連接字串，然後藉由設定 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> 的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>、<xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> 和 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 屬性加以完成。 組態檔的定義如下。  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"   
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
> 您必須在專案中將參考設定至 `System.Configuration.dll`，程式碼才能執行。  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- [連接字串](../../../../docs/framework/data/adonet/connection-strings.md)
- [隱私權和資料安全性](../../../../docs/framework/data/adonet/privacy-and-data-security.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
